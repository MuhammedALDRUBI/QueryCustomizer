# QueryCustomizer
it used to handling a sql statements for each operation that you want - By PHP and for MySQL


## All Methodes usage an Examples are written in QueryCustomizer file (near each method )

<hr> 

## uasble Methodes :

### 1-  __construct() 
     this method will create a new object from ArrayAnalyzer class to use it in arrays analyzing operations
     
## All bellow Methodes will return a query string (string data type)

### 2 - insertQueryCustomizer( string $table , Array $ColumnsAndValuesArray)
    this method will handle an insert sql statment ... it just need :
    @table : table name that you want to insert row into
    
    @ColumnsAndValuesArray : is an associative array that contains the row 's columns and its columns values
    Ex : $ColumnsAndValuesArray = array("Username" => "user123" , "Password" => "224422"); 
    
### 3 - deleteQueryCustomizer( string $table , Array $conditionsArray = array()  , $options = array()  )
    this method will handle a delete sql statment ... it just need :
    @table : table name that you want to delete row from
    
    @conditionsArray : is an indexed array that contains deletion conditions
    it is nullable array BUT if it there no deletion's conditions ALL rows will be deleted
    Ex : $conditionsArray = array("Id = 4");
    
    @option array : it contains : 
    1- "limit" : is a numeric value key ... it mean how many rows will be deleted .. default value null
    Ex $options = array(  "limit" => 2)
    
### 4 - updateQueryCustomizer( string $table , Array $ColumnsValuesArray , Array $conditionsArray = array() , $options = array() ) 
    this method will handle a update sql statment ... it just need :
    @table : table name that contains rows that you want to update it
    
    @ColumnsValuesArray : is an associative array that contains the row 's columns and its columns values
    
    @conditionsArray : is an indexed array that contains updating conditions
     it is nullable array BUT if it there no updating's conditions ALL rows will be updated
    Ex : $conditionsArray = array("Id = 4");
    
    @option array : it contains : 
    1- "limit" : is a numeric value key ... it mean how many rows will be updated .. default value null
    Ex $options = array(  "limit" => 2)
    
### 5 - selectQueryCustomizer( string $table , Array $columnsArray = array(), Array $conditionsArray = array() ,  $options = array() )  
    this method will handle a select sql statment ... it just need :
    @table : table name that you want to select rows from
    
    @columnsArray : is an indexed array that contains the columns these you want to select it from table
    Ex : $columnsArray = array("FirstName" , "LastName" , "Email");
    
    @conditionsArray : is an indexed array that contains selection conditions
     it is nullable array BUT if it there no selection's conditions ALL rows will be selected
    Ex : $conditionsArray = array("Id = 4");
    
    @option array : it contains : 
     1- "limit" : is a numeric value key ... it mean how many rows will be selected .. default value is null
    2- "offset" : is a numeric value key ... it mean From what record do you start counting?  .. default value is null
    Ex $options = array("limit" => 2 , "offset" => 0)
    
### 6 - innerJoinQueryCustomizer( Array $tableAndColumnsOfEachTableAssocArray , Array $JoinConditions , Array $whereConditions = array() , $options = array() )
    this method will handle an inner join sql statment ... it just need :
    @tableAndColumnsOfEachTableAssocArray : is an associative array that contains All tables to be entered into the join process
    AND each table key's value must be an indexed array that contains all columns that wanted from that table
    EX : $tableAndColumnsOfEachTableAssocArray = array("users" => array("FirstName" , "LastName") , "posts" => array("title" , "content"))
    
    @JoinConditions : is an indexde array that contains all join conditions .... it must not be null
    EX : $JoinConditions = array("users.id = posts.UserId" , "posts.id = comment.PostId");
    (don't write and , or in connditions ... it is by "and" by default)
    
    @whereConditions : is an indexed array that contains where conditions that will be applied after join operation is done
    Ex : $whereConditions = array("users.city = 'Istanbul'" , "posts.created_at > '2011-11-13'"); 
    
    @option array : it contains : 
     1- "limit" : is a numeric value key ... it mean how many rows will be selected .. default value is null
    2- "offset" : is a numeric value key ... it mean From what record do you start counting?  .. default value is null
    Ex $options = array("limit" => 2 , "offset" => 0)
    
### 7 - complexJoinQueryCustomizer( Array $tableAndColumnsOfEachTableAssocArray , string $LeftTableName ,  Array $RightTableName_joinType_Array , Array $table_joinConsitions , Array $whereConditions = array() ,  $options = array() ) 
    this method will handle a join sql statment (inner or left or right or all of them) ... it just need :
    @tableAndColumnsOfEachTableAssocArray : is an associative array that contains All tables to be entered into the join process
    AND each table key's value must be an indexed array that contains all columns that wanted from that table
    EX : $tableAndColumnsOfEachTableAssocArray = array("users" => array("FirstName" , "LastName") , "posts" => array("title" , "content"))
    
    @LeftTableName : is the left table name .... that will be joined with other tables (right tables)
    Ex  : $LeftTableName = "users"; ===result will be===> "users inner join otherTable on joinCondition inner join anOtherTable on anOtherJoinCondition"
    
    @RightTableName_joinType_Array : is an Associative array that contains all tables these will be joined with leftTable .... it must not be null
     each table is key , and each key 's value must be a join type like "inner" or "left" or "right"
    EX : $RightTableName_joinType_Array = array("profile" => "inner" , "posts" => "left" , "comments" => "left"); (don't write 'join' in  join type)
    
    @table_joinConsitions : is an Associative array that contains all tables these will be joined with leftTable .... it must not be null
     each table is key , and each key 's value must be join condition
    Ex : $table_joinConsitions = array("posts" => "users.id = posts.UserId" , "comments" => "posts.id = comments.PostId" ); 
    (don't write and , or in connditions ... it is by "and" by default)
    
    @whereConditions : is an indexed array that contains where conditions that will be applied after join operation is done
    Ex : $whereConditions = array("users.city = 'Istanbul'" , "posts.created_at > '2011-11-13'"); 
    
    @option array : it contains : 
     1- "limit" : is a numeric value key ... it mean how many rows will be selected .. default value is null
    2- "offset" : is a numeric value key ... it mean From what record do you start counting?  .. default value is null
    Ex $options = array("limit" => 2 , "offset" => 0)
    
### 8 - unionQueryCustomizer( Array $ArrayOfSelectionQueries , $unionAll = false)
    this method will handle a union sql statment ... it just need :
    @ArrayOfSelectionQueries : is an indexed array that contains all selection statements these will be integrated in a one table
    EX : $ArrayOfSelectionQueries = array("select email from users" , "select email from customers");
    
    if @unionAll is false the values will be unique (No redundancy there in value)
    
### 9 - isColumnFoundQueryCustomizer( string $dbName , string $table , string $column)
    this method will handle a  query to check if table has a specified field or not ... it just need :
    @dbName : database name
    @table : table name
    @column : column or field name

# Don't forget to support us on : 
##  Facebook : https://www.facebook.com/MDRDevelopment/
##  Instagram : https://www.instagram.com/mdr_development_tr/
##  GitHub : https://github.com/MuhammedALDRUBI

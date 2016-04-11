Class methods:
These are chainable, but can only be called on a class or ActiveRecord_Relation. So they can't be chained in just any order - for instance, .count returns an integer and .pluck returns an array, so they should be the last methods called.

Class.all
returns ActiveRecord_Relation (similar to array) of all instances of the class

Class.where(column: search_value)
returns ActiveRecord_Relation (similar to array) of all instances meeting the criteria

Class.where({column1: value1, column2: value2}) OR
Class.where("column1: ? AND column2: ?", value1, value2)
returns ActiveRecord_Relation (similar to array) of all instances meeting the criteria

Class.order(column: :asc/:desc)
returns ordered ActiveRecord_Relation (similar to array)

Class.count
returns integer count of elements in class

Class.pluck(:column1, :column2, etc.)
returns an array of arrays containing these values for every instance of class

Class.first
returns the first instance of the class

Class.find(#id)
returns the instance of the class with the given #id

Class.find_by(column: search_value)
returns the first instance of the class that matches the search criteria



Creating new Records

Class.new(column1: value1, column2: value2, etc.)
Instantiates a new instance of the class. This is not saved in the database. It will not have an #id until it's been saved, so don't give it one. Returns the new instance.

instance.persisted?
Returns boolean announcing if the instance has been persisted in the database.

instance.save
Saves the instance to the database and assigns it an #id. Returns boolean if the instance saved sucessfully.

Class.create(column1: value1, column2: value2, etc.)
Instantiates and saves the new instance simultaneously. Returns the new instance.

Class.create [{column1: value1}, {column1, value2}]
Creates multiple instances at once. Returns and array of the new instances.

Class.find_or_initialize_by(column: value)
Looks for the criteria in the database. If not found, it creates a new instance. Returns the found or initialized instance. Does not save the initialized instance.

Class.find_or_create_by(column: value)
Looks for the criteria in the database. If not found, it creates a new instance. Returns the found or initialized instance. New instances are saved directly to the database.
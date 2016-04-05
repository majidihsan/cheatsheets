
Helpful link
-------------
https://gist.github.com/rstacruz/1569572


Tips and tricks:
-------------------
to automatically destroy detail record when destroy customer record:
has_one :detail, :dependent => :destroy

to destroy chid objects when parent in destroyed, add the following to the parent class:
has_many :children, :dependent => :destroy

to hide child object, add the following to parent class:
delegate :birthday, :gender, :city, :to => :detail



CREATING RECORDS:
=====================

Single/Parent:

myStudent1 = Student.new(:first_name => 'Ann', :last_name => 'Smith', :birthday => '1986-08-11')
	myStudent1.save

Child:

	(myStudent1.classes.new(:name => ‘Geometry’)).save
	##note alternative method for saving and pluralized ‘classes’##


  QUERIES
=====================

Find one by id:
Customer.find(17)

Find related records by id:
Customer.find(17).detail.birthday
## finds birthday field for the customer with id = 17. Birthday field is contained in Details table.


Find by label:
--------------

Can do:
- Person.where(:user_name => user_name).first
- Person.where(:user_name => user_name, :password => password).first

Better:
- Person.find_by_user_name(user_name)
- Person.find_all_by_last_name(last_name)
- Person.find_by_user_name_and_password(user_name, password)


List all:
-----------
Contact.all.each do |contact|
puts contact.first_name
end


Conditional:
--------------
Student.where(:gender => 'male')


LIKE:
-----
Contact.where("first_name LIKE 'A%'")
Contact.where(‘first_name LIKE ?', “A%")


Using LIKE to find values in the middle of a string:
----------------------------------------------------
Student.where("birthday LIKE '%-07-%'").each do |student|
  puts student.first_name + " has a birthday in July"
end


Client.count
------------
Client.where(:first_name => 'Ryan').count


Unique:
--------
Client.select(:name).uniq

A more complicated example using .uniq:

contacts = Address.where(:state => 'CA').includes(:contact).collect do |address|
  address.contact
end

contacts.uniq.each do |contact|
  puts contact
end




Validation Helpers
===================

null: false

presence
disallows null values or empty strings for a given attribute

uniqueness
ensures that only unique values are allowed for a given attribute

numericality
ensures that values contain only the digits 0 through 9

format
checks that values conform to a particular format using regular expressions

length
checks for variety of length attributes, such as minimum, maximum, or within a range.

inclusion
checks that the value for an attribute is included in some set of pre-determined values.

exceller
===============

The Exceller is an Excel creator tool for Django Queryset. 
It create .xls files containing specified data from Django Queryset.


Installation 
===========================================

Install the requirement dependency pyExcelerator to write Excel files from Python::

   % pip install install PyExcelerator

You can install the requirements using the ``pip-requires.txt`` file::

   % pip install -r pip-requires.txt

Move exceller.py file into your django project and that is all

Getting started
---------------

Once installed, created a queryset, if you want to generate an excel
sheet from the content,  you mereley need to instantiate the class
Exceller and run the method create_excel.

Here is a sample. 

Consider the Model:

class Deposit(models.Model):
	
    type = models.CharField(max_length=8, choices= deposit_types)
    bank = models.ForeignKey(Bank)
    name = models.CharField(max_length=100)
    date = models.DateField("Deposit Date")
    amount = models.DecimalField( max_digits=7, decimal_places=1)
    .....

    def __unicode__(self):
       return self.name

    def foo(self):
       return "bar"


Consider that we have say 1000s of deposit records

To create an Excel File follow these steps

from exceller import Exceller

deposits =Deposit.objects.all()

ex= Exceller(deposits, fields =["type", "bank", "name", "date","amount", "foo"], filename ="deposits.xls", path="/var/www/tally/static_media/")
ex.create_excel()

The last command should create the excel file, which you can import it
into your favorite spreadsheet program and mess around with. 
There are couple of helper functions, please see the code for more...

Ensure that you write permissions to the path, and correct spellings of the fields are provided.

There are number of stuff which still needs to be done.I will do that as and when I have time, including integrating tests and exception routines. Also there are couple of advanced classes that lets you create excel documents where data can be spread across multiple sheets.

In case you need some help, assistance, feature requests, suggestions for improvments, please let us know 

Code written by Ramdas S
For more details contact ramdas AT netzary DOT com

Code updated by Emile Bniz NIYIBIZI
For more bniz AT nyaruka DOT com
http://www.nyaruka.com

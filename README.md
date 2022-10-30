# TelephonDirectory
#It is program in python regarding TelephoneDirectory using Mongodb
import pymongo
mongo=pymongo.MongoClient("mongodb://127.0.0.1:27017/")
mydb=mongo['telephone']
mycollection=mydb['telephone_directory']
people_information=[
    {'name':'Advaith','phone_number':12345678,'place':'hyderabad'},
    {'name':'Bala','phone_number':3578956,'place':'banglore'},
    
    {'name':'Diya','phone_number':30789056,'place':'chennai'},
    {'name':'Chandra','phone_number':406745390,'place':'bihar'},
     
    {'name':'Sudeep','phone_number':30789046,'place':'banglore'},
    {'name':'Yamuna','phone_number':40674530,'place':'bihar'},
     
     {'name':'Zakir','phone_number':35789560,'place':'banglore'}
          
     ]
ids=mycollection.insert_many(people_information)
data=mycollection.find({},{'_id':0})
for i in data:
    print(i)

query={'place':'banglore'}
data1=mycollection.find(query)
for i in data1:
    print(i)
    
    
old_value={'name':'Sudeep'}
new_value={'$set':{'name':'sai_sudeep'}}
    
    
old_values={'place':'bihar'}
new_values={'$set':{'place':'patna'}}
mycollection.update_many(old_value,new_value)
data2=mycollection.find({},{'_id':0})
for i in data2:
    print(i)
    
query1={'name':'Zakir'}
mycollection.delete_one(query1)

query2={'place':'banglore'}
mycollection.delete_many(query2)

data3=mycollection.find({},{'_id':0})
for i in data3:
    print(i)

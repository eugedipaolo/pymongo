# pymongo
# Some code to resolve my homeworks of the MongoDB course 

import pymongo
import bottle
import sys
  
connection = pymongo.MongoClient("mongodb://localhost")
db = connection.newDataBase

@bottle.get('/item')
def printItem():

  item = db.newSet.find_one()
  print item['the item']
  
@bottle.get('/collection')
def printCollection():

  try:
    iter = db.find({},limit=1, skip=n).sort('value', direction=1)
    for item in iter:
      return str(int(item['value'])) + "\n"
  except Exception as e:
    print "Error trying to read collection:", type(e), e
   
bottle.debug(True)
bottle.run(host='localhost', port=8080)
  


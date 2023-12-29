# mondo-db-queries
This contains different types of queries performed on json format documents and collections.
Practical answers of mswd:
Practical 1:
Query Documents:
1.	db.movies.find()
2.	db.movies.find({writer:"Quentin Tarantino"})
3.	db.movies.find({actors:"Brad Pitt"})
4.	db.movies.find({franchise:"The Hobbit"})
5.	db.movies.find({year:{$lte:2000}})
6.	db.movies.find({$or:[{year:{$lte:2000}},{year:{$gte:2010}}]})

Update documents:
7.	db.movies.updateOne({title:" The Hobbit: An Unexpected Journey"},{$push:{synopsis:"Arelectant hobbit, Bilbo Baggins, set out to the Lonely Mountain with a spirited group of dwarves to reclaim their mountain home -and the gold within it -from the dragon Smaug"}})
8.	db.movies.updateOne({title:"The Hobbit: The Desolation of Smaug"},{$push:{synopsis:"The dwarves,alone with Bilbo Baggins and Gandalf the Grey, continue their quest to reclaim Erebor,their homeland, from Smaug.BilboBaggins is in possession of a mysterious and magical ring"}})
9.	db.movies.updateOne({title:"Pulp Fiction"},{$push:{actors:"Samuel L. Jackson"}})


Query Documents:
        10. a.) db.movies.find({synopsis:{$regex:"Bilbo"}})  //this will give whole document
b.) db.movies.find({"synopsis": { $regex: "Bilbo"} },{ title: true, _id: false })//this will give just title
            	a.) db.movies.find({"synopsis": { $regex: "Gandalf"} })//this will give whole document
b.) db.movies.find({"synopsis": { $regex: "Gandalf"}},{title:true,id:false} ) //this will give just   title.
11. a)db.movies.find({$and:[{synopsis:{$regex:"Bilbo"}},{$nor:[{synopsis:{$regex:"Gandalf"}}]}]})
b)db.movies.find({$and:[{synopsis:{$regex:"Bilbo"}},{$nor:[{synopsis:{$regex:"Gandalf"}}]}]},{title:true,_id:false})
13.a.) db.movies.find({$or:[{synopsis:{$regex:"dwarves"}},{synopsis:{$regex:"hobbit"}}]})
     b.)db.movies.find({$or:[{synopsis:{$regex:"dwarves"}},{synopsis:{$regex:"hobbit"}}]},{title:true,_id:false})

14.a.)db.movies.find({$and:[{synopsis:{$regex:"gold"}},{synopsis:{$regex:"dragon"}}]})
b.) db.movies.find({$and:[{synopsis:{$regex:"gold"}},{synopsis:{$regex:"dragon"}}]},{title:true,_id:false})

Delete Documents Query:

15. db.movies.deleteOne({title:"Pee Wee Herman's Big Adventure"})

16. db.movies.deleteOne({title:"Avatar"})




Practical 2 queries

1.	db.resturants.find()…..or……. db.resturants.find().pretty
2.	db.resturants.find({},{restaurant_id:true,name:true,borough:true,cuisine:true})
3.	db.resturants.find({},{restaurant_id:true,name:true,borough:true,cuisine:true,_id:false})
4.	db.resturants.find({},{address:{zipcode:true},_id:false})
5.	db.resturants.find({borough:"Brooklyn"},{name:true})
6.	db.resturants.find({borough:"Brooklyn"},{name:true}).limit(5)
7.	db.resturants.find({borough:"Brooklyn"},{name:true}).skip(5).limit(5)
8.	 db.resturants.find({grades:{$elemMatch:{"score":{$gt : 70}}}},{name: true, grades: true, _id: 0})
9.	db.resturants.find({grades:{$elemMatch:{score:{$gt:70,$lt:100}}}},{name:true,score:true, _id:0})
10.	db.resturants.find({$and:[{cuisine:{$ne:"American"}},{grades:{$elemMatch:{score:{$gt:70}}}}]},{name:true,_id:false})
11.	

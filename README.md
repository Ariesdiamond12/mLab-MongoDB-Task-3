# mLab-MongoDB-Task-3

##Library Management System
- created a Library Management System using MongoDB
- open terminal or command prompt and run command "mongosh" to start MongoDB
- to create your database type the command "use LibraryDB"
- then we must create a collections in the database, type the command e.g "db.createCollection('books')"
- in our collection we must have multiple documents , and for that we have to use the insertMany([{}]) command to insert our documnets
- in the LibraryDB database I have 3 collections namely Books, Authors and Patrons

# Books Collection
 db.Books.insertMany([ { _id: 1, title: "1984", author_id: 1, genres: ["Dystopian", "Political Fiction"], published_year: 1949, available: true }, { _id: 2, title: "To Kill a Mockingbird", author_id: 2, genres: ["Southern Gothic", "Bildungsroman"], published_year: 1960, available: true }, { _id: 3, title: "The Great Gatsby", author_id: 3, genres: ["Tragedy"], published_year: 1925, available: true }, { _id: 4, title: "Brave New World", author_id: 4, genres: ["Dystopian", "Science Fiction"], published_year: 1932, available: true }, { _id: 5, title: "The Catcher in the Rye", author_id: 5, genres: ["Realist Novel", "Bildungsroman"], published_year: 1951, available: true }, { _id: 6, title: "Moby-Dick", author_id: 6, genres: ["Adventure Fiction"], published_year: 1851, available: true }, { _id: 7, title: "Pride and Prejudice", author_id: 7, genres: ["Romantic Novel"], published_year: 1813, available: true }, { _id: 8, title: "War and Peace", author_id: 8, genres: ["Historical Novel"], published_year: 1869, available: true }, { _id: 9, title: "Crime and Punishment", author_id: 9, genres: ["Philosophical Novel"], published_year: 1866, available: true }, { _id: 10, title: "The Hobbit", author_id: 10, genres: ["Fantasy"], published_year: 1937, available: true } ])

 # Authors Collection
 db.Authors.insertMany([ { _id: 1, name: "George Orwell", nationality: "British", birth_year: 1903, death_year: 1950 }, { _id: 2, name: "Harper Lee", nationality: "American", birth_year: 1926, death_year: 2016 }, { _id: 3, name: "F. Scott Fitzgerald", nationality: "American", birth_year: 1896, death_year: 1940 }, { _id: 4, name: "Aldous Huxley", nationality: "British", birth_year: 1894, death_year: 1963 }, { _id: 5, name: "J.D. Salinger", nationality: "American", birth_year: 1919, death_year: 2010 }, { _id: 6, name: "Herman Melville", nationality: "American", birth_year: 1819, death_year: 1891 }, { _id: 7, name: "Jane Austen", nationality: "British", birth_year: 1775, death_year: 1817 }, { _id: 8, name: "Leo Tolstoy", nationality: "Russian", birth_year: 1828, death_year: 1910 }, { _id: 9, name: "Fyodor Dostoevsky", nationality: "Russian", birth_year: 1821, death_year: 1881 }, { _id: 10, name: "J.R.R. Tolkien", nationality: "British", birth_year: 1892, death_year: 1973 } ])

# Patrons Collection
 db.Patrons.insertMany([ { _id: 1, name: "Alice Johnson", email: "alice@example.com", borrowed_books: [] }, { _id: 2, name: "Bob Smith", email: "bob@example.com", borrowed_books: [1, 2] }, { _id: 3, name: "Carol White", email: "carol@example.com", borrowed_books: [] }, { _id: 4, name: "David Brown", email: "david@example.com", borrowed_books: [3] }, { _id: 5, name: "Eve Davis", email: "eve@example.com", borrowed_books: [] }, { _id: 6, name: "Frank Moore", email: "frank@example.com", borrowed_books: [4, 5] }, { _id: 7, name: "Grace Miller", email: "grace@example.com", borrowed_books: [] }, { _id: 8, name: "Hank Wilson", email: "hank@example.com", borrowed_books: [6] }, { _id: 9, name: "Ivy Taylor", email: "ivy@example.com", borrowed_books: [] }, { _id: 10, name: "Jack Anderson", email: "jack@example.com", borrowed_books: [7, 8] } ])

 # READ
 - so to READ your data you must use the find() method - this method reads all the documents in MongoDB OR finds all the data in the collection that you have created
 -so in the terminal you are going to type the command e.g db.Books.find() 
   ![Screenshot (10)](https://github.com/user-attachments/assets/6452015b-955d-43c5-87cc-441f6d5be97e)
 - so to find the book specific book by Title "To Kill a Mockingbird" you type db.Books.find({title:"To Kill a Mockingbird"})/
   ![Screenshot (11)](https://github.com/user-attachments/assets/778902df-ac5e-45f4-9c9f-3feef214da74)
- to find all the books with the specific author (author_id:5) type db.Books.find({author_id: 5})
   ![Screenshot (12)](https://github.com/user-attachments/assets/3955e709-f8b2-4f79-afae-a3621971a457)
- to all the available books type db.Books.find({available: true})
   ![Screenshot (13)](https://github.com/user-attachments/assets/e322dd55-4135-4788-b535-eccf6c47b03e)

# UPDATE
- to update Book availability type db.Books.updateOne({_id: 3}, {$set: {available:false}})
![Screenshot (14)](https://github.com/user-attachments/assets/39f36472-b683-4d0c-bc20-086603caf032)
- to add a genre type command db.Books.updateOne({_id: 8}, {$addToSet: {genres: "Documentary"}})
  ![Screenshot (15)](https://github.com/user-attachments/assets/b06bcffc-6d7d-43f9-b3a6-3f76b82b9852)
- to add a borrowed book to the Patron type db.Patrons.updateOne({_id: 5}, {$push: {borrow}})
  ![Screenshot (16)](https://github.com/user-attachments/assets/5d07b74c-9a2c-4aab-a4d8-42a764665e59)

# DELETE
- to delete a book by the title (title: "Brave New World") type db.Books.deleteOne({title: "Brave New World"})
![Screenshot (18)](https://github.com/user-attachments/assets/e4e215d6-144a-4bd7-b534-4cd565492dfb)
- to delete an author (_id: 3) type db.Authors.deleteOne({})
![Screenshot (19)](https://github.com/user-attachments/assets/2516ec7c-0fd6-4603-ade6-725ef5fef540)

# Advanced Queries with Operators
- to find books published after 1950 using $gt type db.Books.find({})
<!-- ScreenShot -->
- to find all american authors using $eq type db.Authors.find({nationality: {$eq: "American"}})
![Screenshot (23)](https://github.com/user-attachments/assets/289e96f7-6638-4ac4-bb67-d07136232065)
- to set all books to available using $set type db.Books.updateMany({}, {$set: {available: true}})

- to all books that are available and published after 1950 type db.Books.find({available: true, published_year: {$gt:1950}})
![Screenshot (24)](https://github.com/user-attachments/assets/59d22c3a-737f-48b1-919d-25c9cc12c9d5)
-to find authors whose name contain "George" type db.Authors.find({name: {$regex: "George", $options:"i"}})
![Screenshot (25)](https://github.com/user-attachments/assets/99e6b740-bf84-4aa1-8a99-21e60b242241)

- to increment the published year of 1869 by 1 type db.Books.updateOne({published_year: 1869}, {$inc: {published_year:1}})
  ![Screenshot (26)](https://github.com/user-attachments/assets/a3a99dac-9e20-4e7b-bd5f-fecb82e8e1ab)

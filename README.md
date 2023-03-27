# Online-Bookstore-project
This code uses the axios library to make a GET request to the /books endpoint of the back-end API, and displays the resulting book data in a list format. Again, this code is just an example and would need to be customized to fit the specific requirements of the project.
import React, { useState, useEffect } from 'react';
import axios from 'axios';

function BookList() {
  const [books, setBooks] = useState([]);

  useEffect(() => {
    async function fetchBooks() {
      const response = await axios.get('/books');
      setBooks(response.data);
    }
    fetchBooks();
  }, []);

  return (
    <div>
      {books.map(book => (
        <div key={book._id}>
          <img src={book.coverImage} alt={book.title} />
          <h3>{book.title}</h3>
          <p>{book.author}</p>
          <p>{book.genre}</p>
          <p>{book.price}</p>
        </div>
      ))}
    </div>
  );
}

export default BookList;

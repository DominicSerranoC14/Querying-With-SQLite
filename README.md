# Querying-With-SQLite
Example queries on the Chinook sample SQLite database.

1. Provide a query showing Customers (just their full names, customer ID and country) who are not in the US.

  `SELECT  FirstName || ' ' || LastName as 'Fullname', CustomerId, Country FROM Customer
  WHERE Country != 'USA'`

2. Provide a query only showing the Customers from Brazil.

  `SELECT * FROM Customer
  WHERE Country = 'Brazil'`

3. Provide a query showing the Invoices of customers who are from Brazil. The resultant table should show the customer's full name, Invoice ID, Date of the invoice and billing country.

  `SELECT Customer.FirstName || ' ' || Customer.LastName as 'CustomerName',` `Invoice.InvoiceId, Invoice.InvoiceDate, Invoice.BillingCountry
  FROM Invoice`
  `JOIN Customer ON Customer.CustomerId = Invoice.InvoiceId`

4. Provide a query showing only the Employees who are Sales Agents.

  `SELECT * FROM Employee
  WHERE "Title" = "Sales Support Agent"`

5. Provide a query showing a unique list of billing countries from the Invoice table.

  `SELECT DISTINCT BillingCountry FROM Invoice`

6. Provide a query showing the invoices of customers who are from Brazil.

  `SELECT Invoice.InvoiceId, Customer.Country
  FROM Invoice`
  `JOIN Customer ON Invoice.CustomerId = Customer.CustomerId`
  `WHERE "Country" = "Brazil"`

7. Provide a query that shows the invoices associated with each sales agent. The resultant table should include the Sales Agent's full name.

  `SELECT Employee.FirstName || ' ' || Employee.LastName as FullName, Invoice.InvoiceId
  FROM Employee`
  `JOIN Customer ON Customer.SupportRepId = Employee.EmployeeId`
  `JOIN Invoice ON Invoice.CustomerId = Customer.CustomerId`
  `ORDER BY InvoiceId ASC
  `

8. Provide a query that shows the Invoice Total, Customer name, Country and Sale Agent name for all invoices and customers.

  `SELECT Invoice.Total,
  Customer.FirstName || ' ' || Customer.LastName AS FullName,`
  `Employee.FirstName || ' ' || Employee.LastName AS AgentName,`
  `Invoice.BillingCountryg
  FROM Invoice`
  `JOIN Customer ON Invoice.CustomerId = Customer.CustomerId`
  `JOIN Employee ON Customer.SupportRepId = Employee.EmployeeId`
  `ORDER BY Total ASC
  `

9. How many Invoices were there in 2009 and 2011?
  What are the respective total sales for each of those years?

  `SELECT Sum(Total), Count(InvoiceDate) FROM Invoice
  WHERE InvoiceDate LIKE '2009%'
  `

  `SELECT Sum(Total), Count(InvoiceDate) FROM Invoice
  WHERE InvoiceDate LIKE '2011%'
  `

10. Looking at the InvoiceLine table, provide a query that COUNTs the number of line items for Invoice ID 37.

  `SELECT InvoiceId, Count(InvoiceLineId) as LineItemQty FROM InvoiceLine
  WHERE InvoiceId = 37
  `

11. Provide a query that includes the track name with each invoice line item.

  `SELECT InvoiceLine.InvoiceLineId, Track.Name
  FROM InvoiceLine`
  `JOIN Track ON InvoiceLine.TrackId = Track.TrackId`
  `ORDER BY InvoiceLineId ASC
  `

12. Provide a query that includes the purchased track name AND artist name with each invoice line item.

  `SELECT InvoiceLine.InvoiceLineId, Track.Name as Track, Artist.Name as Artist
  FROM InvoiceLine`
  `JOIN Track ON InvoiceLine.TrackId = Track.TrackId`
  `JOIN Album ON Track.AlbumId = Album.AlbumId`
  `JOIN Artist ON Album.ArtistId = Artist.ArtistId`
  `ORDER BY InvoiceLineId ASC
  `

13. Provide a query that shows the # of invoices per country. HINT: GROUP BY

  `SELECT BillingCountry, Count(InvoiceId) AS Invoices FROM Invoice
  GROUP BY BillingCountry
  `

14. Provide a query that shows the total number of tracks in each playlist. The Playlist name should be included on the resultant table.

  `SELECT Playlist.Name AS Playlist,
  Count(Track.TrackId) AS Tracks
  FROM Playlist`
  `JOIN PlaylistTrack ON Playlist.PlaylistId = PlaylistTrack.PlaylistId`
  `JOIN Track ON PlaylistTrack.TrackId = Track.TrackId`
  `GROUP BY Playlist
  `

15. Provide a query that shows all the Tracks, but displays no IDs. The resultant table should include the Album name, Media type and Genre.

  `SELECT Track.Name as TrackName,
  Album.Title as AlbumTitle,
  MediaType.Name as MediaType,
  Genre.Name as Genre  
  From Track`
  `JOIN Album ON Track.AlbumId = Album.AlbumId`
  `JOIN MediaType ON Track.MediaTypeId = Track.MediaTypeId`
  `JOIN Genre ON Track.GenreId = Genre.GenreId`


16. Provide a query that shows all Invoices but includes the # of invoice line items.

  `SELECT *,
  InvoiceLine.InvoiceLineId as LineItemNum
  FROM Invoice`
  `JOIN InvoiceLine ON Invoice.InvoiceId = InvoiceLine.InvoiceId`

17. Provide a query that shows total sales made by each sales agent.

  ``

18. Which sales agent made the most in sales in 2009?
19. Which sales agent made the most in sales in 2010?
20. Which sales agent made the most in sales over all?
21. Provide a query that shows the # of customers assigned to each sales agent.
22. Provide a query that shows the total sales per country. Which country's customers spent the most?
23. Provide a query that shows the most purchased track of 2013.
24. Provide a query that shows the top 5 most purchased tracks over all.
25. Provide a query that shows the top 3 best selling artists.
26. Provide a query that shows the most purchased Media Type.

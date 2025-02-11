# Adding EJS Templates (4-adding-ejs)

In this lesson, we'll enhance our pizza ordering site by adding EJS templates. This will allow us to:
- Display dynamic content on our pages
- Create reusable page layouts
- Show order details on the confirmation page
- Create a better admin interface

## Setting Up EJS

1. First, install EJS:
   ```bash
   npm install ejs
   ```

2. Configure Express to use EJS in app.js:
   ```javascript
   app.set('view engine', 'ejs');
   ```

## Creating EJS Templates

1. Rename your confirmation.html to confirmation.ejs and update it to show order details:
   ```html
   <div class="order-details">
       <h2>Order Details</h2>
       <p>Name: <%= order.fname %> <%= order.lname %></p>
       <p>Email: <%= order.email %></p>
       <!-- ... more order details ... -->
   </div>
   ```

2. Update the submit-order route to render the template:
   ```javascript
   app.post('/submit-order', (req, res) => {
       const order = {
           // ... order details ...
       };
       orders.push(order);
       res.render('confirmation', { order });
   });
   ```

## Adding an Admin Interface

1. Create views/admin.ejs with a template for displaying all orders:
   ```html
   <div class="content">
       <h2>All Orders</h2>
       <% if (orders.length === 0) { %>
           <p>No orders yet!</p>
       <% } else { %>
           <% orders.forEach(order => { %>
               <div class="order-card">
                   <h3><%= order.fname %> <%= order.lname %></h3>
                   <!-- ... order details ... -->
               </div>
           <% }); %>
       <% } %>
   </div>
   ```

2. Update the admin route to use the template:
   ```javascript
   app.get('/admin/orders', (req, res) => {
       res.render('admin', { orders });
   });
   ```

## Testing the Changes

1. Start your server and place a test order
2. You should now see order details on the confirmation page
3. Visit /admin/orders to see a nicely formatted list of all orders

## Key EJS Features Used

- `<%= %>` - Outputs escaped HTML
- `<% %>` - Runs JavaScript code
- Conditional rendering with if/else
- Iterating over arrays with forEach

## Troubleshooting

If pages aren't rendering:
- Make sure EJS is installed (`npm install ejs`)
- Verify that the view engine is set correctly
- Check that your .ejs files are in the views directory
- Ensure you're passing the correct data to your templates

If order details aren't showing:
- Check the variable names in your templates match the data you're passing
- Use console.log to verify the data in your routes
- Make sure you're using the correct EJS syntax (<%= vs <%-)

*Note: This tutorial builds on the previous pizza ordering site example.* 
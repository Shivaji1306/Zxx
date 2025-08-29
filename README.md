fcuk — Restaurant Website

Overview
- A 5-page modern responsive restaurant site built with HTML, Tailwind CSS (via CDN), and vanilla JavaScript.
- Pages included: index.html, about.html, contact.html, cart.html, checkout.html.
- Uses a sample default menu and a localStorage-backed cart.
- Payment flow demonstrates a mock Razorpay integration (no real payments). The checkout flow simulates creating an order and completing payment.
- All styling uses Tailwind classes directly in the HTML files. Main content uses fluid full-width layouts (w-full) — no fixed max-width containers.
- Google Font: Poppins (comment format included at top of HTML files).

Images
- Images are placeholders using the format src="https://images.unsplash.com/photo-1588192524634-1c3f8490f68b?crop=entropy&cs=tinysrgb&fit=max&fm=jpg&ixid=M3w3ODkyNDZ8MHwxfHNlYXJjaHw1fHxkZXNjcmlwdGlvbnxlbnwwfDB8fHwxNzU2MzY1MzQxfDA&ixlib=rb-4.1.0&q=80&w=1080". Replace with real image URLs as needed.

How to use
1. Open index.html in a browser. The site is static — no server required for the mock demo.
2. Browse the menu, click Add to place items in the cart. Cart is persisted in localStorage.
3. Go to Cart to modify quantities or remove items.
4. Proceed to Checkout. Fill in billing/delivery details. Choose Razorpay (Mock) or Cash on Delivery.
   - Razorpay (Mock): Simulates creating an order and completing a payment. No real money transferred.
   - COD: Simulates placing a cash-on-delivery order.
5. After a mock successful payment, the cart is cleared and you are redirected to the home page.

Replacing mock Razorpay with real integration
- Real flow (high level):
  1. Your server creates an order via Razorpay Orders API and returns the order_id.
  2. On the client, load Razorpay script: <script src="https://checkout.razorpay.com/v1/checkout.js"></script>
  3. Create options including the real key_id and order_id returned by your server, then call: const rzp = new Razorpay(options); rzp.open();
  4. On payment success, Razorpay will return payment_id, order_id and signature; you must verify signature on your server to ensure payment integrity.

- In checkout.html, replace the mocked createMockOrder and openMockRazorpay with calls to your server and the real Razorpay checkout as described above.

Notes & Security
- This project is a front-end demo. For production use:
  - Do not create Razorpay orders on the client — order creation (and secret key usage) must be done on a server.
  - Always verify Razorpay payment signatures server-side before fulfilling orders.
  - Sanitize and validate user inputs server-side.

Customization
- Update the MENU array inside index.html to change menu items, prices, and descriptions.
- Replace placeholder images (https://images.unsplash.com/photo-1683193063549-b8a50825cbc0?crop=entropy&cs=tinysrgb&fit=max&fm=jpg&ixid=M3w3ODkyNDZ8MHwxfHNlYXJjaHw2fHwuLi58ZW58MHwwfHx8MTc1NjQ0NzQ5NHww&ixlib=rb-4.1.0&q=80&w=1080) with actual image URLs.
- Update currency or price display logic if you need a currency other than INR.

Support
- If you want, I can:
  - Replace mock Razorpay flow with a server + client example (Node/Express) for real order creation and signature verification.
  - Customize styles, colors, or fonts further.
  - Add user accounts, order history, or admin menu management.

Enjoy your new site for fcuk! If you'd like real payment integration help (server-side code), tell me which backend stack you prefer (Node, Python, PHP, etc.) and I can provide the server code to create and verify Razorpay orders.
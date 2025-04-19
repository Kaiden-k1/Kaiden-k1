
```html
<div style="font-family: 'Georgia', serif; max-width: 600px; margin: auto; padding: 20px; border: 1px solid #ddd;">
  <h2 style="color: #800000; text-align: center;">Baccarat</h2>
  <hr>
  <p><strong>Date:</strong> {{date}}</p>
  <p><strong>Customer Name:</strong> {{name}}</p>
  <p><strong>Email:</strong> {{email}}</p>
  <hr>
  <h3>Purchased Items</h3>
  <pre style="white-space: pre-wrap; font-size: 16px;">{{items}}</pre>
  <hr>
  <p><strong>Tax:</strong> ${{tax}}</p>
  <p><strong>Total:</strong> <strong style="font-size: 18px;">${{total}}</strong></p>
  <hr>
  <p style="text-align: center;">Thank you for choosing Baccarat.</p>
</div>
```
document.getElementById("receipt-form").addEventListener("submit", function(e) {
  e.preventDefault();

  const form = this;
  const status = document.getElementById("status");

  const formData = {
    name: form.name.value,
    email: form.email.value,
    date: form.date.value,
    items: form.items.value,
    tax: form.tax.value,
    total: form.total.value
  };

  emailjs.send("YOUR_SERVICE_ID", "YOUR_TEMPLATE_ID", formData)
    .then(() => {
      status.textContent = "Receipt sent successfully!";
      form.reset();
    }, (err) => {
      status.textContent = "Failed to send receipt.";
      console.error(err);
    });
});

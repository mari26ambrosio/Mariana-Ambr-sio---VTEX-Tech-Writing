### **How to create an order invoicing integration**

To invoice an order on the VTEX platform means adding the items' invoice to the Orders module. It is also possible to send a partial invoice when there are changes in the order's value, items, or in cases of item returns. The invoice can be submitted in the following ways:

- Through the invoice submission API;
- Through [**Admin VTEX**](https://help.vtex.com/pt/tutorial/faturar-um-pedido-manualmente--7p1h852V5t54KyscpgxE2v).

Check out our documentation on the [**Order Flow and Status**](https://help.vtex.com/en/tutorial/order-flow-and-status--tutorials_196) in VTEX.

#### Creating an order invoicing integration via API:

Follow the steps below to create an order invoicing integration:

1. If your store has an ERP integration or another integration for managing orders, you will need to create an integration with the VTEX platform. The links below provide an overview of the order integration flow between a back-office system and a VTEX store:

- [Back-office (ERP/PIM/WMS)](https://developers.vtex.com/docs/guides/erp-integration-guide)
- [Set up order integration](https://developers.vtex.com/docs/guides/erp-integration-set-up-order-integration)
- [Set up order processing](https://developers.vtex.com/docs/guides/erp-integration-set-up-order-processing)
- [Change order](https://developers.vtex.com/docs/guides/change-order)
- [FAQ: ERP Integration](https://developers.vtex.com/docs/guides/faq-erp-integration)

2. The connector records the integration status of the order to validate whether the order has been integrated into VTEX, preventing the reprocessing of orders;

3. For orders that have been integrated into VTEX, the connector should check the order status in VTEX using the [**Get Order API**](https://developers.vtex.com/docs/api-reference/orders-api/#get-/api/oms/pvt/orders/-orderId-);

4. To invoice the order, the [**Order invoice notification**](https://developers.vtex.com/docs/api-reference/orders-api#post-/api/oms/pvt/orders/-orderId-/invoice) endpoint must be called, and instead of having the field `type` value defined as `Output`, it will be `Input`:

- [**Order invoice notification**](https://developers.vtex.com/docs/api-reference/orders-api#post-/api/oms/pvt/orders/-orderId-/invoice);

	- This request invoices an order, indicating successful completion and allowing the order status to change to `invoiced`. Once invoiced, the order's status cannot be modified.

- [**Update order's partial invoice (send tracking number)**](https://developers.vtex.com/docs/api-reference/orders-api#patch-/api/oms/pvt/orders/-orderId-/invoice/-invoiceNumber-);

	- Update an order by adding its tracking number to the [**partial invoice**](https://help.vtex.com/en/tracks/pedidos--2xkTisx4SXOWXQel8Jg8sa/q9GPspTb9cHlMeAZfdEUe). After this, you can use the [**Update Order Tracking Status API**](https://developers.vtex.com/docs/api-reference/orders-api#put-/api/oms/pvt/orders/-orderId-/invoice/-invoiceNumber-/tracking) to add tracking events.

- [**Adding a second address for invoicing an order**](https://developers.vtex.com/docs/guides/adding-a-second-address-to-the-order);

	- In B2B transactions, it's common to use an invoicing address different from the delivery address.
	
- [**Formatting order invoicing time via API**](https://developers.vtex.com/docs/guides/formatting-order-invoicing-time);
	- When submitting invoice data to a marketplace via API, use the [**Update Order's Partial Invoice**](https://developers.vtex.com/vtex-rest-api/reference/updatepartialinvoicesendtrackingnumber) endpoint to format the order invoicing time.

### Error Handling and Troubleshooting
When integrating with VTEX, it’s important to handle potential errors gracefully. Common issues include:

- Invalid `orderId` or `invoiceNumber`: Ensure that these identifiers are correct and correspond to an existing order;
- Missing or incorrect fields: Double-check that all required fields are included in the payload and follow the correct format.
  
VTEX will return an error response if the request cannot be processed, typically with an HTTP `400 Bad Request` or `404 Not Found`, along with a message describing the issue. Ensure that your integration includes error logging and retry mechanisms to handle these scenarios.

By following these steps, you can successfully integrate the order invoicing process into VTEX, enabling seamless communication between your system and VTEX’s OMS. This integration supports automatic invoice notifications and the ability to update tracking information for orders shipped in multiple packages.

For further details on the endpoints and additional functionality, refer to the [**VTEX API documentation**](https://developers.vtex.com/docs/guides/orders-overview).

# Alternative APIs - Example Requests

## Webhook Payload Example

This is the payload that Virtualstock will POST to your webhook endpoint:

```json
{
    "channel": "CHANNEL1",
    "carrier": "DPD",
    "dispatched_date": "2019-05-23T00:00:00+0000",
    "estimated_delivery_date": "2019-05-23T00:00:00+0000",
    "order_number": "ORDER121821",
    "tracking_number": "TXD98798798798",
    "tracking_url": "https://www.some.site.com/tracking",
    "status": "DELIVERED",
    "checkpoint_time": "2019-05-23T13:09:51+0000",
    "tracking_message": "Manchester HUB",
    "items": [
        {
            "line_ref": "001",
            "part_number": "sku-002014",
            "quantity": 10
        }
    ],
    "ts": 15484698531106
}
```

## SFTP APIs

For SFTP-based APIs (Flat File CSV, Invoice JSON, Order Events CSV), there are no HTTP request examples as these use file-based transfers over SFTP protocol. Refer to the specific documentation for each SFTP API for file format specifications.

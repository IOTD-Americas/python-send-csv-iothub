# python-send-csv-iothub
Python example that sends simulated telemetry in csv format to iot hub

# send_message_csv.py
```py

    async def send_test_message(i):
        print("sending message #" + str(i))
        message_id=uuid.uuid4()
        csv_text=str(i)+"," + str(message_id) +",test wind speed " + str(i) + "," +datetime.datetime.now().strftime("%d/%m/%Y %H:%M:%S")
        
        msg = Message(csv_text)
        msg.message_id = message_id
        msg.correlation_id = "correlation-1234"
        msg.custom_properties["tornado-warning"] = "yes"
        msg.content_encoding = "utf-8"
        msg.content_type = "application/csv"
        await device_client.send_message(msg)
        print("done sending message #" + str(i))
```
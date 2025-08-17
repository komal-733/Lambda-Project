# Lambda-Project
# Task 1: Create and Configure the Lambda Function
- Navigate to AWS Lambda via the Management Console search bar and click Create function.
- Set Function name to resize_image and Runtime to Python 3.9.
- Under Execution role, select Use an existing role and choose ResizeImageLambdaRole.
- Add the Pillow image-processing layer:
- Scroll to Layers → Add a layer → Custom layers → PillowPythonLambdaLayer → choose its version → Add.
- Replace the default handler code:
- Copy the provided resize_image Python code from the simulation instructions.
- Paste it into lambda_function.py in the console’s Code editor.
- Click Deploy to save your function.
- On the Configuration tab, click Edit, set Memory to 512 MB, and Save.

# Task 2: Add an S3 Trigger
- In the Lambda console’s Function overview, click Add trigger.
- Choose S3 as the trigger type.
- Select the bucket whose name contains “original”.
- Set Event types to “All object create events” and acknowledge Recursive invocation.
- Click Add, then scroll to Triggers → Details to verify the bucket ARN and event types.

# Task 3: Upload an Image and Inspect Results
- Download large-image.jpg to your local machine via the provided link.
- Return to the S3 console, open the “original” bucket, and upload large-image.jpg.
- Verify the resized version appears in the target bucket (name contains “resized”) with a much smaller file size.
- Go to the Lambda console, select resize_image, and open the Monitor tab.
- Under CloudWatch Logs in Recent invocations, expand the most recent entry to review duration, initialization time (cold start), and memory usage.

# Task 4: Optimize Memory for Performance
For each memory setting—1024 MB, 2048 MB, then 3008 MB—do the following:
- In Configuration → General configuration, click Edit, update Memory, and Save.
- Re-upload large-image.jpg to the “original” bucket.
- Return to Monitor → CloudWatch Logs → Recent invocations and note the new duration.
By 3008 MB, the function should complete in approximately 500 ms with the 5 MB image.


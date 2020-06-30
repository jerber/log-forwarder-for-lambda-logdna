#Steps

As a background, read: https://www.serverless.com/blog/serverless-ops-logs.

1. Add an .env file that contains your LogDNA ingension key like so:
   `LOGDNA_KEY=1234ExampleIngestionKey5678`

2. sls deploy

3. sls info -v

4. Copy the arn from ForwarderLambdaFunctionQualifiedArn and remove the `:<number>` at the very end.

5. Paste that arn in your main serverless.yml like so:

```
logForwarding:
    destinationARN: arn:aws:lambda:us-east-1:444719859866:function:log-forwarder-prod-forwarder
    filterPattern: "-[INFO] -RequestId"
```

6. You can now deploy your main function and it should forward your logs to logDNA.

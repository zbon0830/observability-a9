# Observability Assignment (A9)

A small Express to-do app that uses OpenTelemetry to send traces to Jaeger.

- `index.js` - the Express server. It connects to MongoDB and has two routes: `/todo` and `/todo/:id`.
- `tracing.js` - sets up OpenTelemetry and sends traces to Jaeger with the OTLP exporter.

## How to run

1. Install packages:

   ```
   npm install
   ```

2. Start MongoDB:

   ```
   docker run -d -p 27017:27017 mongo
   ```

3. Start Jaeger:

   ```
   docker run -d --name jaeger -p 16686:16686 -p 4317:4317 -p 4318:4318 -p 5778:5778 -p 9411:9411 jaegertracing/jaeger:2.5.0
   ```

4. Start the app:

   ```
   node --require ./tracing.js index.js
   ```

5. Make a request:

   ```
   curl http://localhost:3000/todo
   ```

6. Open http://localhost:16686, choose `todo-service`, and click **Find Traces**.

Screenshots from Jaeger are in the `screenshots` folder.

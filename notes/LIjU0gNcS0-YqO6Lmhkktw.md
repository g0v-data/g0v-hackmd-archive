---
tags:
---

#  Setting Up Distributed Tracing in Angular with Jaeger and OpenTelemetry
Monitoring performance over various services and identifying the bottlenecks in modern-day distributed systems is a challenging feat. However, distributed tracing solves the forwarding policies of requests through several services, simplifying the visualization and debugging of application profiling. For single-page applications (SPAs) such as Angular, in which the individual screen is constantly refreshed, distributed tracing is a prerequisite in helping analyze the effects of frontend interaction towards backend services. This guide will show you how to set up the tracing system in the Angular application through OpenTelemetry and Jaeger and implement distributed tracing as done in other systems. Upon completion, you will be proficient in tracing application interactions in Angular, including covering relevant spans and controlling the requests to the backend systems, which will be presented in Jaeger. Now let’s begin incorporating this fundamental toolkit into our Angular applications for greater insight!

## Prerequisites
Before we start with setting up distributed tracking with Angular, there are a few important tools and configurations that you need. First, make sure you have a rudimentary Angular application created; it will be easier to explain tracing because you already know how the structure of Angular works. You will also need to have Node.js and npm set up because they are required for working with libraries that manage the dependencies and run the OpenTelemetry libraries.

To gather and analyze the traces, we are going to use Jaeger, which is an open-source tool created for distributed tracing operations. You can choose to run Jaeger on your local machine through Docker for ease of installation or go for a hosted solution using the cloud-managed Jaeger instance. Finally, we are going to add some OpenTelemetry libraries meant to be used in Angular for tracing, instrumentation, and tapering of trace data to Jaeger. With these configurations applied, we are good to go with making changes to improve monitoring in your Angular application.

## Understanding Distributed Tracing in Frontend Applications
The process of distributed tracing is paramount when understanding the request flows in an application, especially in microservice architectures. With single-page applications (SPAs) such as Angular apps, where user navigations rely on app transitions, tracing extends beyond only the backend services and includes tracing user actions, providing a holistic view of how users interact with the entire system.

Relative to the front end, distributed tracing can help monitor events like clicking buttons, making an API call, changing navigation, or skipping pages altogether and assign these events to specific back-end services. For example, if an end user makes a request that is sent via the Angular application to a service, tracing will also track the request from the client side, which will be important when trying to diagnose performance degradation and/or failure in connecting both clients and servers.

As for the front-end, Angular now also has tracing capabilities because of tools availed by OpenTelemetry; therefore, an Angular application is ready to link user action or API invocation in Angular with the span, which in tracing indicates one of the activities in a trace. Each span contains information regarding the time an operation begins and ends, the operation’s particulars, and any errors that were encountered during the operation.

So, let's consider a very basic example of how to create a manual span in Angular when you want to make an HTTP request to the API.

```typescript
import { Injectable } from '@angular/core';
import { HttpClient } from '@angular/common/http';
import { trace, context } from '@opentelemetry/api';

@Injectable({
  providedIn: 'root'
})
export class DataService {
  private tracer = trace.getTracer('angular-demo-app');

  constructor(private http: HttpClient) {}

  fetchData() {
    const span = this.tracer.startSpan('fetchData'); // Start a span for the HTTP request
    return this.http.get('/api/data').pipe(
      tap(() => span.end()), // End the span when the request completes
      catchError((error) => {
        span.setStatus({ code: SpanStatusCode.ERROR, message: error.message });
        span.end();
        throw error;
      })
    );
  }
}
```
In this case scenario, for every invocation of `fetchData`, a span named `fetchData` is created, which signifies when the HTTP call is made and when it is finished. In instances where an error happens, it will be captured within the span. This offers a detailed perspective on the interactions from the front end and their impact on the services at the back end. Equipped with this knowledge, let us now proceed to the steps in which we set up Jaeger and OpenTelemetry for achieved tracing implementation.

## Setting Up Jaeger
Jaeger is an open-source distributed tracing system that is widely used to monitor and troubleshoot distributed applications. In this tutorial, we are going to use Jaeger to trace and analyze our Angular application. You can either install and enable Jaeger locally using a Docker container or use a cloud-based managed Jaeger.

To run Jaeger locally, you can execute Docker and a one-liner command. Open a terminal and type:

```bash
docker run -d --name jaeger \
  -e COLLECTOR_ZIPKIN_HTTP_PORT=9411 \
  -p 5775:5775/udp \
  -p 6831:6831/udp \
  -p 6832:6832/udp \
  -p 5778:5778 \
  -p 16686:16686 \
  -p 14250:14250 \
  -p 14268:14268 \
  -p 14269:14269 \
  -p 9411:9411 \
  jaegertracing/all-in-one:1.22
```

This command launches Jaeger in an “all-in-one” mode, which contains all necessary building blocks like the collector, the query service, and the interface with the user, simplifying the getting started stage. After the container is up and running, one can access the Jaeger UI by simply opening the browser and typing in the URL http://localhost:16686. The UI allows performing trace queries, trace ID filtering, and deep analysis of the spans.

To check that Jaeger is functioning as intended, one may examine the UI, which states that following the start of the trace dispatching application side, there is a section that contains several traces, the last few ones, sent by the client application. Further on, we will adjust OpenTelemetry in Angular to forward traces’ data to Jaeger, thus allowing for the end-to-end visibility of the whole application, frontend and backend communications included.

## 5. Integrating OpenTelemetry in Angular
In order to capture and export traces from your Angular application, it is necessary to implement OpenTelemetry. This includes installing the following open telemetry packages in the former scenario along with configurations to ensure traces are sent and stored in Jaeger with their automatic instrumentation for typical actions like HTTP requests.

First, add to the dependencies of your Angular app the OpenTelemetry libraries:

```bash
npm install @opentelemetry/api @opentelemetry/sdk-trace-web @opentelemetry/auto-instrumentations-web @opentelemetry/exporter-trace-otlp-http
```

Now that you’ve included these packages, you can use OpenTelemetry to enable tracing in your application at the very beginning of its execution. Here’s an example of how to perform this operation in the primary Angular module.

```typescript
import { NgModule } from '@angular/core';
import { BrowserModule } from '@angular/platform-browser';
import { AppComponent } from './app.component';
import { HttpClientModule } from '@angular/common/http';
import { trace, context } from '@opentelemetry/api';
import { WebTracerProvider } from '@opentelemetry/sdk-trace-web';
import { registerInstrumentations } from '@opentelemetry/auto-instrumentations-web';
import { OTLPTraceExporter } from '@opentelemetry/exporter-trace-otlp-http';

@NgModule({
  declarations: [AppComponent],
  imports: [BrowserModule, HttpClientModule],
  bootstrap: [AppComponent]
})
export class AppModule {
  constructor() {
    const provider = new WebTracerProvider();
    const exporter = new OTLPTraceExporter({
      url: 'http://localhost:9411/api/v2/spans' // Endpoint for Jaeger or another collector
    });

    provider.addSpanProcessor(new SimpleSpanProcessor(exporter));
    provider.register();

    registerInstrumentations({
      tracerProvider: provider,
      instrumentations: [
        new HttpClientInstrumentation(), // Automatically instruments Angular HTTP client requests
      ],
    });
  }
}
```

In this configuration, we create `WebTracerProvider` and include `OTLPTraceExporter` sending spans to Jaeger along with `registerInstrumentations`, which help in the instrumentation of HTTP requests through Angular’s `HttpClient`, preventing any loss of traces. This captures every trace of each HTTP call, making it possible to visualize how the front end communicates with the back end.

By now we’ve learned that the OpenTelemetry starts with the Angular application, where the application sends traces via every HTTP call to Jaeger. In the subsequent sections, we’ll look at how it is possible to enhance the ability to trace the spans across the Angular application by adding individual spans and context propagation.

## Creating Custom Spans and Context Propagation
After successfully integrating OpenTelemetry, you can go a step further than just automatic instrumentation and add your own custom spans in order to monitor specific actions or user events in an Angular application. Custom spans give you more precision on what is traced since you can span some specific operations or code sections that are useful for performance evaluation.

To include a custom span, it’s possible to simply begin and end one manually within a particular section of code. For instance, if one needs to determine the duration of an internal operation inside a service method, the tracer can be used:

```typescript
import { Injectable } from '@angular/core';
import { trace } from '@opentelemetry/api';

@Injectable({
  providedIn: 'root'
})
export class ExampleService {
  private tracer = trace.getTracer('angular-custom-tracer');

  performOperation() {
    const span = this.tracer.startSpan('performOperation'); // Start a custom span
    try {
      // Execute your operation here
      console.log('Performing an operation that we want to trace...');
    } finally {
      span.end(); // End the span once the operation is complete
    }
  }
}
```

Here, `performOperation` is the name of the span created just before the different operation is performed and closed immediately after that, thus holding the duration of the operation in Jaeger. This type of custom span helps you narrow down the tracing to areas of specific functions that are not automatically instrumented.

To make sure that a particular trace context is passed while moving from one different service or component to another (for example, calling a backend service from the front end), one can employ context propagation. OpenTelemetry takes care of this generally for HTTP requests; therefore, when an HTTP request goes out from your Angular application, the trace context gets passed inside the request headers. If you want to solve the problem of context propagation for the non-blocking operations in Angular, the context API of OpenTelemetry will allow you to do that:

```typescript
import { Injectable } from '@angular/core';
import { HttpClient } from '@angular/common/http';
import { trace, context } from '@opentelemetry/api';

@Injectable({
  providedIn: 'root'
})
export class DataService {
  private tracer = trace.getTracer('angular-data-service');

  constructor(private http: HttpClient) {}

  fetchData() {
    const span = this.tracer.startSpan('fetchData');
    return context.with(trace.setSpan(context.active(), span), () => {
      return this.http.get('/api/data').pipe(
        finalize(() => span.end())
      );
    });
  }
}
```

In this `fetchData` method, the custom span is associated with the HTTP request so that the trace context is sent to the backend, from where it is possible to link it with other services. This allows request flows to be visualized seamlessly between the frontend and backend services.

After configuring custom spans and context propagation, your Angular application already writes extensive traces, enabling deep analysis of individual interactions. In the following sections, we’ll examine how these traces can be tested to confirm their correctness in Jaeger.

## Testing and Verifying Traces in Jaeger
After you have completed the configuration of OpenTelemetry and configured Jaeger as the tracing destination, the next step is to ensure that the Angular application is generating and exporting traces. In other words, testing this feature means performing activities in the app that generate traces and looking at them in the Jaeger UI.

First, open your Angular application and carry out a couple of interactable actions of the user, such as pressing a few buttons or requesting data from a backend service, which will trigger HTTP requests. Each of these activities should be producing spans now from the additional mechanisms and its custom installation that you have incorporated.

After that, using your preferred browser, go to http://localhost:16686. and access the Jaeger UI. In the Jaeger UI, choose your Angular application from the services menu, which should have been made available by the name you provided to OpenTelemetry (angular-demoon-app). After that, you can also look for some traces that were generated on your system not long ago. You should get a trace list that includes the traces for the UA actions you executed in the Angular application.

Select a certain trace so that you can see its characteristics. In the trace view, you will see the different spans that make up the operation, custom spans like fetchData or performOperation, and system-generated spans like HTTP request spans. Each span displays its duration together with its start time and any additional information; therefore, it would be straightforward to spot areas of latency or even where the bottleneck is in the trace.

In addition, if you do not see traces, be sure to check your OpenTelemetry configuration, that Jaeger is up and running, and whether the OTLPTraceExporter URL is specified correctly. After this point, traces will function as they should, and you will have a fully functional tracing system that covers your Angular application from beginning to end, tracking its performance and resolving any problems that may arise with it.

## Advanced Configuration and Optimizations


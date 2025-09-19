# Frontend data requests

* goal
  * `BackendSrv` at high level

* [BackendSrv](/grafana/packages/grafana-runtime/src/services/backendSrv.ts)
  * handles
    * ALL Grafana's outgoing HTTP requests  

## Cancel requests

* == data sources / implement their OWN cancellation mechanism
  * Reason:🧠DIFFERENT needs / EACH data source🧠

* use cases
  * data request / take a long time to finish
    * POSSIBLE cons
      * | [request starts, request finishes],
        * user can change context
          * _Example:_ user navigate away OR issue the SAME request AGAIN
      * create unnecessary load | data sources

### Request cancellation by Grafana version

* _request cancellation_
  * == Grafana's concept /
    * cancel any ongoing request / ❌Grafana does NOT need❌
    * depend on Grafana version

#### BEFORE Grafana 7.2

* TODO: Before Grafana can cancel any data request, it has to identify that request
* Grafana identifies a request using the property `requestId` [passed as options](https://github.com/grafana/grafana/blob/main/packages/grafana-runtime/src/services/backendSrv.ts#L47) when you use [BackendSrv](https://github.com/grafana/grafana/blob/main/packages/grafana-runtime/src/services/backendSrv.ts).

The cancellation logic is as follows:

- When an ongoing request discovers that an additional request with the same `requestId` has started, then Grafana will cancel the ongoing request.
- When an ongoing request discovers that the special "cancel all requests" `requestId` was sent, then Grafana will cancel the ongoing request.

#### AFTER Grafana 7.2

Grafana 7.2 introduced an additional way of canceling requests using [RxJs](https://github.com/ReactiveX/rxjs)
* To support the new cancellation functionality, the data source needs to use the new `fetch` function in [BackendSrv](https://github.com/grafana/grafana/blob/main/packages/grafana-runtime/src/services/backendSrv.ts).

Migrating the core data sources to the new `fetch` function is an ongoing process
* To learn more, refer to [this issue](https://github.com/grafana/grafana/issues/27222).

## Request queue

* if Grafana is NOT configured / support HTTP/2 -> browsers / connect with HTTP 1.1
  * restriction
    * \<= [4, 8] parallel requests
      * if some requests take longer -> they will 
        * block later requests
        * make interacting -- with -- Grafana / very slow

* [how to enable HTTP/2 support](/grafana/docs/sources/setup-grafana/configure-grafana/_index.md#protocol)
  * allows
    * MORE parallel requests

### BEFORE Grafana 7.2

Not supported.

### AFTER Grafana 7.2

Grafana uses a _request queue_ to process all incoming data requests in order while reserving a free "spot" for any requests to the Grafana API.

Since the first implementation of the request queue doesn't take into account what browser the user uses, the request queue's limit for parallel data source requests is hard-coded to 5.

> **Note:** Grafana instances [configured with HTTP/2](https://grafana.com/docs/grafana/latest/administration/configuration/#protocol) have a hard-coded limit of 1000.

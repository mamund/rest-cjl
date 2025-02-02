# REST-JCL

working examples of RESTful job conttrol language

## Interfaces

### Service Interface
Below is the abstract service interface that **all** RJCL workflow-compliant services **MUST** support:

```javascript
const rjcl = {
  executeTask() {
    return true;
  },
  repeatTask() {
    return true;
  },
  revertTask() {
    return true;
  },
  continueJob() {
    return true;
  },
  rerunJob() {
    return true;
  },
  cancelJob() {
    return true;
  }
};
```

### Web API Interface
For web-based APIs, the above operations need to be exposed as affordances. Both the client/agent and the service need to understand these `name` values. It is up to the client/agent to activate the proper operation at the right time.

```html
<body>
  <form name="executeTask" ...></form>
  <form name="repeatTask" ...></form>
  <form name="revertTask" ...></form>
  <form name="continueJob" ...></form>
  <form name="rerunJob" ...></form>
  <form name="cancelJob" ...></form>
</body>
```

The protocol details (method, media-type, etc.) will be supplied at runtime by the Web server. It is up to the Web client/agent to understand the details of the affordance and to act accordingly. 


</body>

# REST-JCL

working examples of RESTful job conttrol language

## Interfaces

### Shared Operations
The actions composable services need to support are:

* **Execute** : The actual work (_task_) to be done (e.g., applySalesTax).
* **Repeat** : Repeat the _task_ again in an idempotent manner (e.g., applySalesTax can be safely repeated and still be the same expected results).
* **Revert** : The ability to undo a completed _task_ (e.g., revertSalesTax).
* **Continue** : The ability to stop a _job_ and then, after some pause, continue where you left off to complete the work.
* **Rerun** : The ability to start the _job_ from the beginning and rerun all the steps even if the workflow has been run before.
* **Cancel** : The ability to cancel a running _job_. This might be due to an error in processing, missing state data, a time-out condition, etc.

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

### Additional Operations
Along with the RJCL-specific operations, there are other actions that all workflow-compliant services **MUST** support:

* Home
* GetJobList
* GetJob
* GetTaskList
* GetTask
* ReadState
* WriteState
* TaskStatus
* JobStatus

## Message Formats
All work is done by passing messages between parties.

### RJCL Format
The document that holds job lists

### Job Item Format
The document that defines/describes a job

### Task Item Format
The document that defines/describes a task

### Shared State Format
The document that defines/describes the start state for a job



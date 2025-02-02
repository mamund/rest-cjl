# REST-JCL

working examples of RESTful job conttrol language

## Service Interface
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


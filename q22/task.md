## Task

Team Sunny needs to identify some of their Pods in Namespace `sun`:

1. Add label `protected: true` to all Pods with label `type: worker` OR `type: runner`
2. Add annotation `protected: do not delete this pod` to all Pods that now have label `protected: true`

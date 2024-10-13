---
Source Filename: obj_core_queue_executor
Dependencies: 
Inherits: 
tags:
  - TODO
cssclasses:
  - Atom
aliases:
---
# Snippets
## Creating executor - sequence

```js
queue_executor_NAME = obj_core_queue_timer_executor.create_queue_executor_sequence();
```

## Creating executor - one time execution/alarm like

```js
queue_executor_NAME = obj_core_queue_timer_executor.create_queue_executor();
```

## Creating queue task (work for sequence and OTE)

```js
queue_executor_NAME.enqueue(new QueueTimerTask(TIMER, self.id, function () {	
	// EXECUTION
}, []));
```
# About


```js

queue.enqueue(new QueueTimerTask(2, self.id, function () {	
	sequence_active = true;
}, []));
```

```js
new QueueTimerTask(frame, self.id, function () {	
	// execute
}, [])
```
# TODO
- [ ] TODO
# Attributes

# Methods

# Events
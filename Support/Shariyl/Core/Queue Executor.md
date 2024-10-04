
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
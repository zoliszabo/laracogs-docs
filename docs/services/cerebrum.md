# Cerebrum

The easiest way to add some mental magic to any part of your Laravel/Lumen app.

* Memory provides magic caching abilities.
* Linguistics provides a means of simple NLP.

## Memory Example
```php
use Yab\Cerebrum\Memory;

class TaskService
{
    use Memory;

    public function __construct(TaskRespository $taskRepository)
    {
        $this->repository = $taskRepository;
        // provided by Memory
        $this->memoryDuration(15);
        $this->forgetful([
            'all'
        ]);
    }

    public function all()
    {
        return $this->remember($this->repository->all());
    }

    public function findById($id)
    {
        return $this->remember($this->repository->findById($id));
    }

    public function update($id, $data)
    {
        $this->forget($id);
        return $this->repository->update($id, $data);
    }
}
```

Regarding `$this->forgetful` if you do not set it, then `Memory` will parse your class for all functions and clear any related caches it can find.

The `remember` function on the other hand, will collect a value and store it in the cache,
returning the cached version. The `forget` with a parameter will find caches with similar values and clear your caches.

## Linguistics Example
```php
use Yab\Cerebrum\Linguistics;

class TaskService
{
    use Linguistics;

    public function __construct(TaskRespository $taskRepository)
    {
        $this->repository = $taskRepository;
    }

    public function getKeyWords($id)
    {
        return $this->getKeyWords($this->repository->findById($id)->text);
    }

    public function search($searchString)
    {
        if ($this->isQuestion($seachString)) {
            return $this->repository->search();
        }
    }
}
```

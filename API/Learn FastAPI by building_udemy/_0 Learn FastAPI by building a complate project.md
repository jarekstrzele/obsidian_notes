#udemy  #fastapi  #ivanova_kenova_ines

# Intro
[[1 Working with DBs]]
[[2 Schemas (pydantic models)]]



## Concurrency and async / await
https://fastapi.tiangolo.com/async/#asynchronous-code


### async await example
code:
```python
import asyncio
import time


def sync_count(sleep_time):
    print(f"One with sleep_time {sleep_time}")
    time.sleep(sleep_time)
    print(f"Two with sleep_time {sleep_time}")


def sync_main():
    for num in (2,1,3):
        sync_count(num)


async def async_count(sleep_time):
    print(f"One with sleep_time {sleep_time}")
    await time.sleep(sleep_time)
    print(f"Two with sleep_time {sleep_time}")


async def async_main():
    await asyncio.gather(async_count(2), async_count(1), async_count(3))


start = time.time()
#sync_main()
asyncio.run(async_main())
end =time.time()
elapsed = end - start
print(f"{__file__} executed in {elapsed:0.2f} seconds")




```

sync output:
```shell
One with sleep_time 2
Two with sleep_time 2
One with sleep_time 1
Two with sleep_time 1
One with sleep_time 3
Two with sleep_time 3
/home/jarek/MEGAsync/0PROG/Python/LearnFastAPI_udemy/async.py executed in 6.00 seconds

```

async output:
```shell
One with sleep_time 2
One with sleep_time 1
One with sleep_time 3
Two with sleep_time 1
Two with sleep_time 2
Two with sleep_time 3
/home/jarek/MEGAsync/0PROG/Python/LearnFastAPI_udemy/async.py executed in 3.00 seconds

```




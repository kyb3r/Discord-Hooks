
<h1 align="center">Discord Webhooks</h1>

<div align="center">
    <strong><i>Interact with discord webhooks using python.</i></strong>
</div>
<br>
<div align="center">
    This <strong>simple</strong> library enables you to easily format discord messages and send them to a channel using a webhook url. Synchronous requests as well as asynchronous requests are supported within the library through an easy to use API.
</div>




### Installation
To install the library simply use [pipenv](http://pipenv.org/) (or pip, of course).

```
pipenv install dhooks
```

### Simple Example:

<img src='https://i.imgur.com/8wu283y.png' align='right' width='380' height='125'>

```py
from dhooks import Webhook

hook = Webhook('WEBHOOK_URL')

hook.send("Hello there! I'm a webhook :open_mouth:")
```

### Asynchronous Usage:

To asynchronously make requests using aiohttp, simply pass in `is_async=True` as a parameter when creating a Webhook object. An example is as follows.

```py
import asyncio
from dhooks import Webhook

async def main():
    hook = Webhook('WEBHOOK_URL', is_async=True)
    await hook.send('hello') # sends a message to the webhook channel

loop = asyncio.get_event_loop()
loop.run_until_complete(main())
```



### Discord Embeds:
You can easily format and send embeds using this library. [**Result**](https://i.imgur.com/8Ms4OID.png)
```py
from dhooks import Webhook, Embed


hook = Webhook('WEBHOOK_URL')

embed = Embed(
    description='This is the **description** of the embed! :smiley:'
    color=0x1e0f3,
    timestamp=True # sets the timestamp to current time
    )

embed.set_author(name='Author Goes Here', icon_url='https://i.imgur.com/rdm3W9t.png')
embed.add_field(name='Test Field',value='Value of the field \U0001f62e')
embed.add_field(name='Another Field',value='1234 😄')
embed.set_footer(text='Here is my footer text', icon_url='https://i.imgur.com/rdm3W9t.png')

embed.set_thumbnail('https://i.imgur.com/rdm3W9t.png')
embed.set_image('https://i.imgur.com/f1LOr4q.png')

hook.send(embeds=embed)
```
### Modify Webhooks
You can change the default name and avatar of a webhook easily.
```py
with open('img.png', rb) as f:
    img = f.read() # bytes like object
    
hook.modify(name='Bob', avatar=img) 
```

### Get Webhook Info
```py
hook.get_info()
# the following attributes are now populated with data from discord
hook.guild_id
hook.channel_id
hook.default_name
hook.default_avatar # or hook.default_avatar_url
```

# Delete Webhooks
```py
hook.delete()
```
### License
This project is licensed under MIT

### Contributing
Feel free to contribute to this project, a helping hand is always appreciated.


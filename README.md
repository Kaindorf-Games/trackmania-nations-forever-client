# TrackMania Nations Forever Client

This Python client is intended to be used with the TM Nations Forever remote procedure endpoint.

## Usage Example

```python
from gbx_remote_client import GbxRemoteClient as TMClient
import asyncio

async def main():
  HOST = 'localhost'
  PORT = 5000

  client = TMClient(HOST, PORT)
  await client.connect()
  print('Connected!')
  await client.authenticate('SuperAdmin', 'SuperAdmin')
  print('Authenticated!')

  version = await client.execute('GetVersion')
  print(f'Version: {version}')
  status = await client.execute('GetStatus')
  print(f'Status: {status}')
  response = client.execute('system.listMethods')
  print(f'Methods: {response}')
  player_list = await client.execute('GetPlayerList', 100, 0)
  print(f'Players: {player_list}')


if __name__ == '__main__':
  loop = asyncio.get_event_loop()
  loop.run_until_complete(main())
```

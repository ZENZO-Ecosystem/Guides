# Account

Account-Related Endpoints

## Account Information

Returns an object of the API Account's data. Example: Username, ID, profit / sales from game trading and purchases

`x-www-urlencoded POST https://arcade.zenzo.io/api/v1/account`

Body:
```
api_key: your_api_key
```

## Ping

`x-www-urlencoded POST https://arcade.zenzo.io/api/v1/ping`

Body:
```
api_key: your_api_key
```

## Regen

Regenerates a new API key and destroys the previous key

`x-www-urlencoded POST https://arcade.zenzo.io/api/v1/regen`

Body:
```
api_key: your_api_key
```

# Forge

ZENZO Arcade Forge-Related Endpoints

The Forge API is a partition of the ZENZO API that interacts with the ZENZO Arcade Forge, a service for providing multi-platform, secure and valuable items and content within games. Using the Forge, you can create in-game items that are worth real monetary value. All Forge items are backed by a specific minimum or a user-chosen amount of ZNZ (above set minimum), locked away until the items are either Smelted or Crafted.

The Forge can, for example:

- **Allow gamers to create and introduce truly custom in-game items.**

- **Allow gamers to 'own' their items entirely and permanently.**

- **Allow gamers and game developers to transfer their items to any other account on the network.**

- **Allow game developers to create a network of games where the items within them can be transferred between them, effortlessly.**

## Create

Creates a Forge item

`x-www-urlencoded POST https://arcade.zenzo.io/api/v1/forgecreate`

Body:
```
api_key: your_api_key
title: item_name
value: item_value
image: item_image_url
```

## List

List Forge items owned by your API key's account

`x-www-urlencoded POST https://arcade.zenzo.io/api/v1/forgelist`

Body:
```
api_key: your_api_key
```

## Transfer

Transfer a Forge item to another ZENZO Arcade user

`x-www-urlencoded POST https://arcade.zenzo.io/api/v1/forgetransfer`

Body:
```
api_key: your_api_key
item: item_id
receiver: user_id
```

## Craft

Crafts a new Forge item out of two previously-owned items. The name and image of the new item can be fully customized

`x-www-urlencoded POST https://arcade.zenzo.io/api/v1/forgecraft`

Body:
```
api_key: your_api_key
itemOne: item_id
itemTwo: item_id
name: new_item_name
image: new_item_image_url
```

## Smelt

Smelt (destroy or dissolve) a Forge item. The value of the item in ZNZ will be transferred to your ZENZO Arcade blockchain account

`x-www-urlencoded POST https://arcade.zenzo.io/api/v1/forgesmelt`

Body:
```
api_key: your_api_key
item: item_id
```

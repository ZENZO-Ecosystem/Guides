# Account

Account related endpoints

## Ping

`x-www-urlencoded POST https://arcade.zenzo.io/api/v1/ping`

Body:
```
api_key: your_api_key
```

## Regen

Regenerates a new API Key and destroys the previous Key

`x-www-urlencoded POST https://arcade.zenzo.io/api/v1/regen`

Body:
```
api_key: your_api_key
```

# Forge

Arcade Forge related endpoints

The Forge API is a partition of the ZENZO API that interacts with the Arcade Forge, a service for providing multi-platform, secure and valuable items and content within games. Using the Forge, you can create in-game items that are worth real monetary value, as all Forge items are backed by a specified amount of ZNZ, locked away until the item is either Smelted or Crafted.

The Forge can, for example:

- **Allow gamers to create and introduce truly custom in-game items.**

- **Allow gamers to 'own' their items entirely and permanently.**

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

List Forge items owned by your API Key's account

`x-www-urlencoded POST https://arcade.zenzo.io/api/v1/forgelist`

Body:
```
api_key: your_api_key
```

## Transfer

Transfer a Forge item to another Arcade user

`x-www-urlencoded POST https://arcade.zenzo.io/api/v1/forgetransfer`

Body:
```
api_key: your_api_key
item: item_id
receiver: user_id
```

## Craft

Crafts a new Forge item out of two previously-owned items, the name and image of the new item can be fully customized

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

Smelt (Destroy) a Forge item, the value of the item in ZNZ will be transferred to your Arcade blockchain account

`x-www-urlencoded POST https://arcade.zenzo.io/api/v1/forgesmelt`

Body:
```
api_key: your_api_key
item: item_id
```

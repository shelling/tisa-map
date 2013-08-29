# Tisa-map

這個專案是為了兩岸服務貿易協定所開始的一個專案，目前這個網站會把所有會受到協定衝擊的公司列在這個 map 上，還有會讓一般民眾可以上傳抗議標語，然後把它羅列在這個 map 上面。



# Tech 

## L.Geocoder

origin from [https://github.com/smeijer/L.GeoSearch](https://github.com/smeijer/L.GeoSearch)


## twcompany parser

https://github.com/ronnywang/twcompany

https://github.com/chilijung/twcompany-parser

## data

[data from dropbox](https://www.dropbox.com/sh/o8uu84oskzcsxnp/Do-TEZcra1)

http://company.g0v.ronny.tw/

data folder is from ronnywang's data https://github.com/ronnywang/twcompany , remake is after parser https://github.com/chilijung/twcompany-parser


# Develop

## Backend Setup

1. install ruby. version 1.9 or later of recommendation

2. `$ gem install bundler`

3. `$ bundle install`

4. `unicorn -p port` to run

## Database schema

    Column   |          Type          |                     Modifiers
    ---------+------------------------+----------------------------------------------------
    id       | integer                | not null default nextval('store_id_seq'::regclass)
    location | geometry(Point,4326)   |
    name     | character varying(128) |
    business | text                   |
    taxid    | character(8)           |
    address  | text                   |

## API

1. 以中心點和半徑搜尋 Point
    example: /lng/121.745957/lat/25.133235/radius/100

1. 以所營事業項目搜尋 Point

1. 以公司名稱搜尋 Point
    example: /name/三通報關通運有限公司

1. 以統一編號搜尋 Point
    example: /taxid/00000000

* 返回值都是 GeoJSON

### Stylus

我們現在換到用 stylus 請更改在 `src/css` 裡面的 `*.styl`

http://learnboost.github.io/stylus/

先 install stylus 

``` 
   $ [sudo] npm install [-g] stylus
```

sudo 和 -g for global

要 compile 成 css 用

```
   $ stylus -w -c main.styl
```

`-w` for watching files
`-c` for compressing files

License: MIT http://g0v.mit-license.org/

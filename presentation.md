---
theme: ./
---

# Django Quant Tick

個人プロジェクトの紹介

---

# These slides are at Connpass. So you can check them out.

スライドはConnpassにアップされています。 是非みてください。

---

# Who am I?

お前誰?

---

# My name is Alex, and I'm from Canada 🇨🇦

アレックスです。カナダから来ました。

---
layout: image-right
text: My username on Connpass is globophobe.
trans: Connpassのユーザ名はglobophobeです。
href: https://github.com/globophobe
caption: globophobe 
---

<img class="m-auto border-radius" style="max-width: 80%;" src="/assets/arex.jpg" />

---

# I am a full-remote engineer at <a href="https://creditengine.jp/"><img class="inline" style="height: 4rem;" src="/assets/credit-engine.svg" alt="Credit Engine" /></a>.

<a href="https://creditengine.jp/">クレジットエンジン</a>のフルリモートエンジニアです。

---

# I write code with Django and Vue.js for a SaaS used by banks and other major companies.

DjangoとVue.jsで銀行や大企業が利用しているSaaSを開発しています。

---

# If you are interested, our recruitment information is at <a href="https://www.wantedly.com/companies/creditengine">Wantedly</a>.

興味がある方、採用情報は<a href="https://www.wantedly.com/companies/creditengine">Wantedly</a>にあります。

---
layout: image-right
text: A few years ago, I became interested in this book.
trans: 数年前、この本に興味になりました。
href: https://www.amazon.co.jp/Advances-Financial-Machine-Learning-Marcos/dp/1119482089/
---

<img class="m-auto" style="max-width: 80%;" src="/assets/afml.jpg" />

---
layout: image-right
text: Currently, it is published in Japanese.
trans: 現在、日本語で出版されています。
href: https://www.amazon.co.jp/%E3%83%95%E3%82%A1%E3%82%A4%E3%83%8A%E3%83%B3%E3%82%B9%E6%A9%9F%E6%A2%B0%E5%AD%A6%E7%BF%92-%E3%83%9E%E3%83%AB%E3%82%B3%E3%82%B9%E3%83%BB%E3%83%AD%E3%83%9A%E3%82%B9%E3%83%BB%E3%83%87%E3%83%BB%E3%83%97%E3%83%A9%E3%83%89/dp/4322134637/
---

<img class="m-auto" style="max-width: 60%;" src="/assets/afml-japanese.jpg" />

---

# I became obsessed with chapter 2.

第２章に執着なってしまいました。

---

# Chapter 2 is about Financial Data Structures.

第2章は財務データについてです。

---

# The most popular representation of financial price data is time based Japanese candlestick charts. 

金融価格データは一般的に時間ベースローソク足チャートで表示されます。

---
layout: image-right
text: Candlesticks contain open, high, low, and close data.
trans: ローソク足には、始値、高値、安値、終値のデータがあります。
---

<img class="m-auto" style="max-width: 90%;" src="/assets/candle.jpg" />

---
layout: image-right
text: There are up candles, and down candles.
trans: 色によって、ローソク足の動向が分かります。
---

<img class="m-auto" style="max-width: 90%;" src="/assets/candle-up-down.png" />

---

# However, there are problems with time based candlesticks.

しかし、時間ベースローソク足には問題があります。

---

# According to Lopez de Prado, time based sampling should be avoided because:
Pradoさんによると、時間ベースを避ける理由：

---

# (1) First, markets do not process information at a constant time interval. 

取引の数は時間によって、時々多い、時々すくないです。

---

# For example, there are more trades at market open and close then at any other time during the day. 

例、TradFiの取引は一日の最初と最後の数分には多量行われます。

---

# (2) Second, time-sampled series often exhibit poor statistical properties.

時間ベースサンプリングは正規分布には近くないデータが得られます。

---

# For this reason, Lopez de Prado recommends tick, volume, or dollar-based bars.

なんので、ティック、ボリューム、またはドルベースのローソク足が勧められています。

---

# A new candlestick is created after a threhold value is reached.

しきい値に達するとローソク足を作成されます。

---
layout: code
text: For example, tick bars might create a new bar every 1000 transactions...
trans: たとえば、ティックのローソク足だと、1000トランザクション毎に、
---

<table>
  <tr>
    <td>998</td>
    <td>999</td>
    <td>1000</td>
  </tr>
  <tr>
    <td>...</td>
    <td>...</td>
    <td>Tick bar</td>
  </tr>
</table>

---
layout: code
text: And, dollar bars might create a new bar every &dollar;1,000,000
trans: そして、ドルのローソク足は1,000,000ドル毎に作成されます。
---

<table>
  <tr>
    <td>$999,998</td>
    <td>$999,999</td>
    <td>$1,000,000</td>
  </tr>
  <tr>
    <td>...</td>
    <td>...</td>
    <td>Dollar bar</td>
  </tr>
</table>

---

# When the markets are moving quickly, there will be more data points...

取引が多いときに、より多くのデータポイントが作成され。。。

---

# And, when markets are moving slowly, there will be fewer data points.

そして、取引がすくないときに、データポイントが少なくなります。

---

# Tick, volume, or dollar bars could be useful for algorithmic trading.

ティック、ボリューム、またはドルベースのローソク足はbotterに良いかも知れません。

---
layout: code
text: But, there are challenges...
trans: 課題があります
---

1. Tick data is necessary to create such bars, and can be expensive.
   * 取引データが必要です。お金をかかる可能性があります。
2. Creating the bars is computationally expensive.
   * 作成には計算コストがかかります。 

---
layout: code
text: Solutions
trans: 解決
---

1. Cryptocurrency exchanges often provide tick data for no charge, by API or S3 bucket.
   * 仮想通貨取引所はよく取引データを無料でAPIかS3で提供しています。
2. Aggregating the data can reduce the computational cost.
   * データを集約して、計算コストを削減する事が出来ます。

---

# To resolve those challenges, I developed <a style="text-decoration: none;" href="https://github.com/globophobe/django-quant-tick">Django Quant Tick</a>.

課題を解決するために、<a style="text-decoration: none;" href="https://github.com/globophobe/django-quant-tick">Django Quant Tick</a>を開発しました。

---

# <a style="text-decoration: none;" href="https://github.com/globophobe/django-quant-tick">django-quant-tick</a> downloads and aggregates high frequency trading data.

<a style="text-decoration: none;" href="https://github.com/globophobe/django-quant-tick">django-quant-tick</a>は取引所のデータをダウンロード集約してローソク足を作成されます。

---

# Raw ticks are aggregated if equal `symbol`, `timestamp`, `nanoseconds` and `tickRule`.

`symbol`、`timestmap`、`nanoseconds`、そして`tickRule`は同じの場合、複数の取引は集約されます。

---
layout: code
text: In the second sample, <code>"ticks"&#58; 4</code> indicates the data point was aggregated from 4 transactions.
trans: ２番目のデータポイントは４つの取引から集約されました。
---

```json
{ "timestamp": 1620000915.31424, "price": "57064.01", "volume": "566.6479018604", "notional": "0.00993004", "tickRule": -1, "ticks": 1 },
{ "timestamp": 1620000915.885381, "price": "57071.2", "volume": "9376.6869202914", "notional": "0.16429813", "tickRule": 1, "ticks": 4 }
```

---

# As described in the accompanying project <a style="text-decoration: none;" href="https://github.com/globophobe/cryptofeed-werks">cryptofeed-werks</a>, aggregating trades in this way can increase information, as they are either orders of size or stop loss cascades.

付随するプロジェクト<a style="text-decoration: none;" href="https://github.com/globophobe/cryptofeed-werks">cryptofeed-werks</a>で説明通り、このようにデータを集約されると、データに成行注文とストップロスカスケードの影響が反映されます。

---

# As well, the number of data points can be reduced by 30-50%

そして、データポイントの数は３〜５割までで削減するのを可能になります。

---

# By filtering those data points, for example by `min_volume >= 1000`, the number of can be reduced more.

データポイントを、たとえば `min_volume >= 1000`で、フィルタリングしたら、その数はより減らすことが出来ます。

---
layout: code
text: The first data point from before is aggregated with the second.
trans: 一番最初の例データポイントは２番めと結合されます。
---

```json
"timestamp": 1620000915.885381,
"price": "57071.2",
"volume": "9376.6869202914",
"notional": "0.16429813",
"tickRule": 1,
"ticks": 4,
"high": '57071.2',
"low": '57064.01',
"totalBuyVolume": "9376.6869202914",
"totalVolume": "9943.3348221518",
"totalBuyNotional": "0.16429813",
"totalNotional": "0.17422817",
"totalBuyTicks": 4,
"totalTicks": 5
```

---

# So, 5 ticks have been aggregated into 1 data point.

５の取引は１のデータポイントに集約されました。

---

# Regardless of `min_volume`, <br /><a style="text-decoration: none;" href="https://github.com/globophobe/django-quant-tick">django-quant-tick</a> also aggregates the final data point of each minute, so that 1 minute time based candlesticks can also be derived.

`min_volume`は関係なく、<br /><a style="text-decoration: none;" href="https://github.com/globophobe/django-quant-tick">django-quant-tick</a>が各分の最終データポイントも集約するため、1分の時間ベースのローソク足も導出できます。

---
layout: code
text: In such case, <code>volume</code>, <code>notional</code>, <code>tickRule</code>, and <code>ticks</code> are <code>None</code>.
trans: その場合、関連がある値は <code>None</code> になります。
---

```json
"timestamp": 1620000915.885381,
"price": "57071.2",
"volume": None,
"notional": None,
"tickRule": None,
"ticks": None,
"high": '57071.2',
"low": '57064.01',
"totalBuyVolume": "9376.6869202914",
"totalVolume": "9943.3348221518",
"totalBuyNotional": "0.16429813",
"totalNotional": "0.17422817",
"totalBuyTicks": 4,
"totalTicks": 5
```

---
layout: code
text: django-quant-tick assumes&#58;
trans: 基本仮定：

---

1. Only aggregated data need be stored.
   * 集約されているデータのみを保存
2. Databases can become expensive. S3 and GCS are cheap.
   * データベースは高いです。S3とGCSは安いです。
3. The minimum possible data should be saved in the database, e.g. pagination keys.
   * 可能な限り最小限のデータをデータベースに保存するべきです。たとえば、ページネーションキーなど。

---

# One caveat, as described in the [notes](https://github.com/globophobe/django-quant-tick/blob/main/NOTES.md), data quality is a priority. More so than storage costs.

ストレージについて、[書いてあります](https://github.com/globophobe/django-quant-tick/blob/main/NOTES.md)けど、ストレージコストよりもデータ品質が優先です。

---

# The minimum time interval that <a style="text-decoration: none;" href="https://github.com/globophobe/django-quant-tick">django-quant-tick</a> collects data is 1 minute.

<a style="text-decoration: none;" href="https://github.com/globophobe/django-quant-tick">django-quant-tick</a>はデータ収集の最低限の時間間隔は1分です。

---

# The reason is that aggregated data is validated using the volume of 1 minute time based candlesticks from the exchange API.

理由は集約されているデータは取引所のAPIから取得されている１分時間ベースローソクのボリュームで検証されています。

---

# Another caveat, S3 and GCS storage operations at 1 minute intervals can become expensive.

ストレージについて、もう一点、１分毎にデータを保存すると、S3とGCSのコストが高くなります。

---

# Whenever possible, <a style="text-decoration: none;" href="https://github.com/globophobe/django-quant-tick">django-quant-tick</a> partitions data at 1 hour intervals.

出来るだけ、 <a style="text-decoration: none;" href="https://github.com/globophobe/django-quant-tick">django-quant-tick</a>は1時間毎にデータを保存します。

---

# An hour of data can typically be downloaded, aggregated, validated, and saved within minutes or seconds.

一時間分は通常に数分または数秒以内にダウンロード、集約、検証、そして保存が出来ます。

---

# <a style="text-decoration: none;" href="https://github.com/globophobe/django-quant-tick">django-quant-tick</a> is intended for serverless deployment. The demo deploys to GCP Cloud Run, with GCP Cloud Scheduler for periodic execution.

サーバーレスデプロイは想定です。デモはGCP Cloud Runにデプロイされています。定期的に実行のために、GCP Cloud Schedulerを利用されます。

---

# Basically, dollar bars are created by looping through the aggregated data with a `for loop`.

簡単に言うと、ドルベースのローソク足は`for loop`で行一つ一つの値を数えて作成されています。

---

# They can be generated much faster by aggregating and filtering the data beforehand.

前もってデータを集約されてフィルタリングでデータの量を縮小すると、より早く作成をするのが可能になります。

---

# One might think that dollar bars created from raw ticks rather than aggregated data would be be more precise.

ドルベースのローソク足は集約されているデータで作成するよりも集約されていないデータで作成するのは正確だと思ってしまうかも知りませんけど、

---
layout: code
text: However, the final transaction frequently exceeds the threshold.
trans: 一番最後の取引はしばしばしきい値を超えます。
---

<table>
  <tr>
    <td>$999,998</td>
    <td>$999,999</td>
    <td>$1,099,999</td>
  </tr>
  <tr>
    <td>...</td>
    <td>...</td>
    <td>Dollar bar<br />
      <ul style="font-size: 0.75rem;">
        <li>Threshold is $1,000,000
          <ul style="list-style-type: circle;"><li>しきい値は$1,000,000です</li></ul>
        </li>
        <li>Final transaction was $100,000
          <ul style="list-style-type: circle;"><li>最後の取引は$100,000でした</li></ul>
        </li>
      </ul>
    </td>
  </tr>
</table>

---

# For tick bars, raw ticks are absolutely better, and can be created by looping, for example in steps of 1000.

ティックのローソク足の場合、集約されていないデータは一番いいです。たとえば1000ステップでループする事で簡単に作成が出来ます。

---

# Before [MlFinlab](https://github.com/hudson-and-thames/mlfinlab) changed their license, in a PR I wondered about their use of a for loop.

[MlFinlab](https://github.com/hudson-and-thames/mlfinlab)はライセンスを変更した前に、PRを出した時に、MlFinLabの`for loop`でドルベースのローソク足の作成方法は一番早い方法かどうかは疑問でした。

---

# But after the fact, had to concede, there isn't much alternative.

しかし、それ以降、より早く方法思い付けませんでした。

---

# So, I created django-quant-tick.

なんので、django-quant-tick<br />の開発を始まりました。

---

# As an aside, regarding cryptocurrency exchange APIs...

仮想通貨の取引所のAPIについて。。。

---
layout: image-right
text: Some of them are totally donkey balls (crazy).
trans: ちょっと狂っているAPI仕様も存在すると思います。
---

<img class="m-auto" src="/assets/donkey-balls.jpg" />

---

# For example, the FTX API for trades is paginated by timestamp, max 30 requests per second, 200 max results per request.

たとえば、FTXの取引データAPIの仕様はタイムスタンプページ化、1秒あたり最大30リクエスト、リクエストごとに最大200件の結果です。

---

# The good: 30 requests per second.
良い事： 1秒あたり最大30リクエスト

# The bad: 200 results per request.
悪い事： リクエストごとに最大200件

---

# Usually, the earliest timestamp in the result is the next pagination key.

大体、結果の一番最初のタイムスタンプは次のリクエストのページネーションキーです。

---

# Unfortunately, the FTX API occasionally returns more than 200 trades with the same timestamp.

残念ながら、FTXのAPIは時々、同じタイムスタンプが付いている取引を200件以上を返します。

---

# In such case, the `pagination_id` needs to be adjusted a small amount until unique trades are captured again.

その場合、ユニークデータを収集が出来るために、`pagination_id`パラメータをちっことずつ調整するのが必要です。

---
layout: code
text: An extremely ugly but effective solution, adjusting microseconds&#58;
trans: その解決とは：
---

```python
if len(data) == MAX_RESULTS and not len(unique):
    pagination_id -= 1e-6
    return round(pagination_id, 6)
```

---

# ちょっとだけみてみましょう！

---

# That's all thanks for listening!

以上です。ご清聴ありがとうございます。


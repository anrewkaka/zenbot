![zenbot logo](https://rawgit.com/deviavir/zenbot/master/assets/logo.png)

> “To follow the path, look to the master, follow the master, walk with the master, see through the master, become the master.”
> – Zen Proverb

# Zenbot [![Build/Test Status](https://travis-ci.org/DeviaVir/zenbot.svg?branch=master)](https://travis-ci.org/DeviaVir/zenbot) [![Greenkeeper badge](https://badges.greenkeeper.io/DeviaVir/zenbot.svg)](https://greenkeeper.io/)

## Trạng thái hiện tại

Zenbot 4 là một chức năng, nhưng sẽ khó khăn trong việc tạo ra lợi nhuận. Ở thời điểm này, **Tôi muốn khuyên bạn là không nên trade với khoản tiền lớn** cho đến khi các vấn đề dưới đây được giải quyết:

- Có nhiều người đã báo cáo là [đã thua lỗ trong live trading](https://github.com/carlos8f/zenbot/issues/189) ngay cả khi kết quả mô phỏng là tích cực.
- Đây là ưu tiên hàng đầu của tôi ngay lúc này, vì là 1 con bot không lợi nhuận. Tuy nhiên xin hãy hiểu rằng việc tạo ra lợi nhuận thì rất là khó khăn hơn là tạo ra 1 mô phỏng thực tế.
- Việc thua lỗ có thể là do chiến lược mặc định(`default strategy`) không hoạt động tốt trong điều kiện thị trường đi ngang (non-trending), hoặc là do độ trễ trong giao dịch hoặc là cả hai. Hiện tại thì tôi khuyên bạn không nên sử dụng Zenbot khi mà thị trường non-trending hoặc là thị trường đang có xu hướng giảm.
- Chiến lược `limit-order` mà Zenbot sử dụng để tránh lệ phí của taker, có xu hướng bị điều kiện và sự chậm trễ. Một chế độ sử dụng `markte-type` có lẽ sẽ cần phải được thực hiện, có thể làm cho các chiến lược `frequent-trade` ít khả thi hơn do phí, nhưng thực hiện đáng tin cậy hơn.
- Một tính năng sắp tới sẽ cho phép Zenbot sử dụng một số lượng hạn chế số dư của bạn, thứ mà sẽ giúp ích cho việc thử nghiệm giao dịch live trading, đồng thời giảm thiểu những tổn thất có thể xảy ra từ các yêu cầu nêu trên.

Zenbot là một dự án sở thích cho tôi và tôi xin lỗi vì tôi không thể cống hiến bản thân mình toàn thời gian cho nó. Vì tôi trở nên bận rộn, sự phát triển có thể chậm lại một chút từ đây, vì vậy hãy kiên nhẫn nếu các sự cố không được khắc phục ngay.

## Câu hỏi
Vui lòng hởi những câu hỏi liên quan đến lập trình Zenbot tại stackoverflow với tag là [zenbot](https://stackoverflow.com/questions/tagged/zenbot).

## Mô tả

Zenbot là 1 trading bot dùng để trade cryptocurrency bằng command-line, được xây dựng bằng Node.js và MongoDB.

### Chức năng

- Giao dịch hoàn toàn tự động dựa trên [phân tích kỹ thuật](http://stockcharts.com/school/doku.php?id=chart_school:technical_indicators:introduction_to_technical_indicators_and_oscillators)
- Hỗ trợ hoàn toàn cho [GDAX](https://gdax.com/), [Poloniex](https://poloniex.com), [Kraken](https://kraken.com/), [Bittrex](https://bittrex.com/), [Quadriga](https://www.quadrigacs.com), [Gemini](https://www.gemini.com), [Bitfinex](https://www.bitfinex.com), [CEX.IO](https://cex.io/trade) và [Bitstamp](https://www.bitstamp.net/), và đang tiến hành cho những sàn giao dịch khác
- Kiến trúc dạng plugin để hiện thực việc hỗ trợ các sàn giao dịch và viết thêm chiến lược mới.
- Simulator dùng cho [chiến lược Backtesting](https://gist.github.com/carlos8f/b09a734cf626ffb9bb3bcb1ca35f3db4) chống lại dữ liệu lịch sử
- Chế độ trading "Paper", hoạt động trên mô phỏng dựa trên số dư khi xem live trading
- Có thể cấu hình cho sell stops, buy stops, và (trailing) profit stops
- Thời kỳ lấy mẫu linh hoạt và tần suất trade - trung bình 1-2 trades/ngày trong khoảng 1h, 15-50/ngày trong khoảng 5m

## Disclaimer

- Zenbot thì ko phải là 1 cổ máy sinh lợi nhuận vì vậy nếu sử dụng thì hãy chấp nhận rủi ro
- Crypto-currency thì vẫn đang dc thí nghiệm, và Zenbot thì cũng như vậy. Nghĩa là cả 2 đều có thể `hy sinh` bất cú lúc nào.
- Chạy 1 con bot và trade nói chung cần nghiên cứu cẩn thận về các rủi ro và các thông số liên quan. Một thiết lập sai có thể gây ra một sự mất mát lớn.
- Đừng quên theo dõi Zenbot trong thời gian dài. Zenbot nó ko biết khi nào nên dừng, do đó hãy sẵn sàng để ngăn chặn nó nếu quá nhiều mất mát xảy ra.
- Thường thì các thông số thương mại mặc định sẽ kém hơn so với chuiến thuật buy-hold. Do đó, hãy chạy một số mô phỏng và tìm các thông số tối ưu cho bạn trước khi "all-in".

## Khởi động

### Step 1) Yêu cầu

- Git
- Docker

### Step 2) Cài đặt và cấu hình

Checkout source code

```
git clone https://github.com/anrewkaka/zenbot.git
```

Tạo file thiết lập `conf-sample.js` thành `conf.js`:

```
cp conf-sample.js conf.js
```

- Chỉnh sửa `conf.js`.
- Có thể sử dụng Zenbot trong chế độ "paper trading" mà ko cần bất kỳ thay đổi nào.
- Bạn cần add exchange API keys để trade thực tế.
- API keys thì ko cần quyền deposit/withdrawl.

### Chạy Zenbot

Cần thiết cài đặt Docker, DockerCompose theo như hướng dẫn ở [đây](https://docs.docker.com/compose/install/)

Sau khi cài đặt thì chạy Zenbot

```
cd zenbot
docker-compose up (gắn option -d nếu ko muốn hiển thị log)
```

Nếu mà dùng docker trên windows thì thực thi bằng command bên dưới.

```
docker-compose --file=docker-compose-windows.yml up
```

Nếu muốn chạy command (e.g. backfills, list-selectors), thì cũng có thể thực hiện sau khi hoàn thành command `docker-compose up -d`:

```
docker-compose exec server zenbot list-selectors
docker-compose exec server zenbot backfill <selector> --days <days>
```

#### Cập nhật docker

Thực thi command bến dưới để cập nhật docker

```
docker pull deviavir/zenbot:unstable
```
và sau đó thực thi `docker-compose up -d` để bắt đầu với image mới.

## Selectors

`selector` là định danh để Zenbot biết được sẽ hoặt động trên sàn giao dịch nào và cặp tiền tệ nào. Sử dụng format là `{exchange_slug}.{asset}-{currency}`. Có thể xem list `selector` mà Zenboot hỗ trợ bằng command bên dưới:

```
zenbot list-selectors

gdax:
  gdax.BTC-EUR   (BTC/EUR)
  gdax.BTC-GBP   (BTC/GBP)
  gdax.BTC-USD   (BTC/USD)
  gdax.ETH-BTC   (ETH/BTC)
  gdax.ETH-USD   (ETH/USD)
  gdax.LTC-BTC   (LTC/BTC)
  gdax.LTC-USD   (LTC/USD)

poloniex:
  poloniex.AMP-BTC   (Synereo AMP/BTC)
  poloniex.ARDR-BTC   (Ardor/BTC)
  poloniex.BCN-BTC   (Bytecoin/BTC)
  poloniex.BCN-XMR   (Bytecoin/XMR)
  poloniex.BCY-BTC   (BitCrystals/BTC)

...etc
```

## Chạy simulator cho `selector`

Để xây dựng data thì thực thi command như bên dưới (chọn sàn giao dịch mà có hỗ trợ):

```
zenbot backfill <selector> --days <days>
```

Bạn cũng có thể chọn ngày bắt đầu(start) và ngày kết thúc(end):

```
zenbot backfill <selector> --start="YYYYMMDDhhmm" --end="YYYYMMDDhhmm"
```
Hãy nhớ rằng bạn cũng có thể sử dụng chúng tách biệt với nhau.

Sau khi data đã được xây dựng thì bạn có thể chạy mô phỏng:

```
zenbot sim <selector> [options]
```

Để hiển thị các tùy chọn của `sim` thì dùng command bên dưới:

```
zenbot sim --help

```

Để biết các chiến thuật thì dùng command bên dưới:

```
zenbot list-strategies
```

- Mặc định thì `sim` sẽ thực thi với 1000 đơn vị currency. Để thay đổi thì dùng options `--currency_capital` và `--asset_capital`.
- Mở file `sim_result.html` trên browser để xem biểu đồ.

### Screenshot và kết quả ví dụ

Zenbot đưa ra một biểu đồ HTML của mỗi kết quả mô phỏng. Trong ảnh chụp màn hình bên dưới, mũi tên màu hồng tượng trưng cho việc mua bot (mũi tên lên) và bán (mũi tên xuống) khi nó lặp lại dữ liệu lịch sử của sản phẩm BTC / USD của [GDAX](https://gdax.com/).

![screenshot](https://cloud.githubusercontent.com/assets/106763/25983930/7e5f9436-369c-11e7-971b-ba2916442eea.png)

```
end balance 2954.50 (195.45%)
buy hold 1834.44 (83.44%)
vs. buy hold 61.06%
110 trades over 91 days (avg 1.21 trades/day)
```

Zenbot bắt đầu với $1,000 USD và kết thúc với $2,954.50 sau 90 ngày, tạo 195% lợi nhuận! Mặc dù chiến lược buy/holders đã mang lại 83.44%, Zenbot có tiềm năng lớn trong việc đánh bại buy/holders.

- Lưu ý rằng ví dụ này sử dụng các thiết lập tinh chỉnh để đạt được sự nhận được tối ưu: `--profit_stop_enable_pct=10`, `--profit_stop_pct=4`, `--trend_ema=36`, và `--sell_rate=-0.006`. Tham số mặc định đem lại khoảng 65% lợi nhuận.
- [Dữ liệu nguyên thủy](https://gist.github.com/carlos8f/b09a734cf626ffb9bb3bcb1ca35f3db4) từ việc mô phỏng

## Running zenbot

The following command will launch the bot, and if you haven't touched `c.selector` in `conf.js`, will trade the default BTC/USD pair on GDAX.

```
zenbot trade [--paper] [--manual]
```

Use the `--paper` flag to only perform simulated trades while watching the market.

Use the `--manual` flag to watch the price and account balance, but do not perform trades automatically.

Here's how to run a different selector (example: ETH-BTC on Poloniex):

```
zenbot trade poloniex.eth-btc
```

For a full list of options for the `trade` command, use:

```
zenbot trade --help

  Usage: trade [options] [selector]

  run trading bot against live market data

  Options:

    --conf <path>                   path to optional conf overrides file
    --strategy <name>               strategy to use
    --order_type <type>             order type to use (maker/taker)
    --paper                         use paper trading mode (no real trades will take place)
    --manual                        watch price and account balance, but do not perform trades automatically
    --currency_capital <amount>     for paper trading, amount of start capital in currency
    --asset_capital <amount>        for paper trading, amount of start capital in asset
    --avg_slippage_pct <pct>        avg. amount of slippage to apply to paper trades
    --buy_pct <pct>                 buy with this % of currency balance
    --buy_max_amt <amt>             buy with up to this amount of currency balance
    --sell_pct <pct>                sell with this % of asset balance
    --markdown_buy_pct <pct>        % to mark down buy price (previously the --markup_pct property)
    --markup_sell_pct <pct>         % to mark up sell price (previously the --markup_pct property)
    --order_adjust_time <ms>        adjust bid/ask on this interval to keep orders competitive
    --order_poll_time <ms>          poll order status on this interval
    --sell_stop_pct <pct>           sell if price drops below this % of bought price
    --buy_stop_pct <pct>            buy if price surges above this % of sold price
    --profit_stop_enable_pct <pct>  enable trailing sell stop when reaching this % profit
    --profit_stop_pct <pct>         maintain a trailing stop this % below the high-water mark of profit
    --max_sell_loss_pct <pct>       avoid selling at a loss pct under this float
    --max_slippage_pct <pct>        avoid selling at a slippage pct above this float
    --rsi_periods <periods>         number of periods to calculate RSI at
    --poll_trades <ms>              poll new trades at this interval in ms
    --currency_increment <amount>   Currency increment, if different than the asset increment; e.g. 0.000001
    --disable_stats                 disable printing order stats
    --reset_profit                  start new profit calculation from 0
    --debug                         output detailed debug info
    -h, --help                      output usage information
```

and also:

```
zenbot list-strategies

bollinger
  description:
    Buy when (Signal ≤ Lower Bollinger Band) and sell when (Signal ≥ Upper Bollinger Band).
  options:
    --period=<value>  period length, same as --period_length (default: 1h)
    --period_length=<value>  period length, same as --period (default: 1h)
    --min_periods=<value>  min. number of history periods (default: 52)
    --bollinger_size=<value>  period size (default: 20)
    --bollinger_time=<value>  times of standard deviation between the upper band and the moving averages (default: 2)
    --bollinger_upper_bound_pct=<value>  pct the current price should be near the bollinger upper bound before we sell (default: 0)
    --bollinger_lower_bound_pct=<value>  pct the current price should be near the bollinger lower bound before we buy (default: 0)

cci_srsi
  description:
    Stochastic CCI Strategy
  options:
    --period=<value>  period length, same as --period_length (default: 20m)
    --period_length=<value>  period length, same as --period (default: 20m)
    --min_periods=<value>  min. number of history periods (default: 30)
    --ema_acc=<value>  sideways threshold (0.2-0.4) (default: 0.03)
    --cci_periods=<value>  number of RSI periods (default: 14)
    --rsi_periods=<value>  number of RSI periods (default: 14)
    --srsi_periods=<value>  number of RSI periods (default: 9)
    --srsi_k=<value>  %K line (default: 5)
    --srsi_d=<value>  %D line (default: 3)
    --oversold_rsi=<value>  buy when RSI reaches or drops below this value (default: 18)
    --overbought_rsi=<value>  sell when RSI reaches or goes above this value (default: 85)
    --oversold_cci=<value>  buy when CCI reaches or drops below this value (default: -90)
    --overbought_cci=<value>  sell when CCI reaches or goes above this value (default: 140)
    --constant=<value>  constant (default: 0.015)
If you have questions about this strategy, contact me... @talvasconcelos

crossover_vwap
  description:
    Estimate trends by comparing "Volume Weighted Average Price" to the "Exponential Moving Average".
  options:
    --period=<value>  period length, same as --period_length (default: 120m)
    --period_length=<value>  period length, same as --period (default: 120m)
    --emalen1=<value>  Length of EMA 1 (default: 30)
    --smalen1=<value>  Length of SMA 1 (default: 108)
    --smalen2=<value>  Length of SMA 2 (default: 60)
    --vwap_length=<value>  Min periods for vwap to start (default: 10)
    --vwap_max=<value>  Max history for vwap. Increasing this makes it more sensitive to short-term changes (default: 8000)

dema
  description:
    Buy when (short ema > long ema) and sell when (short ema < long ema).
  options:
    --period=<value>  period length (default: 1h)
    --min_periods=<value>  min. number of history periods (default: 21)
    --ema_short_period=<value>  number of periods for the shorter EMA (default: 10)
    --ema_long_period=<value>  number of periods for the longer EMA (default: 21)
    --up_trend_threshold=<value>  threshold to trigger a buy signal (default: 0)
    --down_trend_threshold=<value>  threshold to trigger a sold signal (default: 0)
    --overbought_rsi_periods=<value>  number of periods for overbought RSI (default: 9)
    --overbought_rsi=<value>  sold when RSI exceeds this value (default: 80)
    --noise_level_pct=<value>  do not trade when short ema is with this % of last short ema, 0 disables this feature (default: 0)

forex_analytics
  description:
    Apply the trained forex analytics model.
  options:
    --modelfile=<value>  modelfile (generated by running `train`), should be in models/ (default: none)
    --period=<value>  period length of a candlestick (default: 30m), same as --period_length (default: 30m)
    --period_length=<value>  period length of a candlestick (default: 30m), same as --period (default: 30m)
    --min_periods=<value>  min. number of history periods (default: 100)

macd
  description:
    Buy when (MACD - Signal > 0) and sell when (MACD - Signal < 0).
  options:
    --period=<value>  period length, same as --period_length (default: 1h)
    --period_length=<value>  period length, same as --period (default: 1h)
    --min_periods=<value>  min. number of history periods (default: 52)
    --ema_short_period=<value>  number of periods for the shorter EMA (default: 12)
    --ema_long_period=<value>  number of periods for the longer EMA (default: 26)
    --signal_period=<value>  number of periods for the signal EMA (default: 9)
    --up_trend_threshold=<value>  threshold to trigger a buy signal (default: 0)
    --down_trend_threshold=<value>  threshold to trigger a sold signal (default: 0)
    --overbought_rsi_periods=<value>  number of periods for overbought RSI (default: 25)
    --overbought_rsi=<value>  sold when RSI exceeds this value (default: 70)

neural
  description:
    Use neural learning to predict future price. Buy = mean(last 3 real prices) < mean(current & last prediction)
  options:
    --period=<value>  period length - make sure to lower your poll trades time to lower than this value. Same as --period_length (default: 1m)
    --period_length=<value>  period length - make sure to lower your poll trades time to lower than this value. Same as --period (default: 1m)
    --activation_1_type=<value>  Neuron Activation Type: sigmoid, tanh, relu (default: sigmoid)
    --neurons_1=<value>  Neurons in layer 1 Shoot for atleast 100 (default: 1)
    --depth=<value>  Rows of data to predict ahead for matches/learning (default: 1)
    --selector=<value>  Selector (default: Gdax.BTC-USD)
    --min_periods=<value>  Periods to calculate learn from (default: 1000)
    --min_predict=<value>  Periods to predict next number from (default: 1)
    --momentum=<value>  momentum of prediction (default: 0.9)
    --decay=<value>  decay of prediction, use teeny tiny increments (default: 0.1)
    --threads=<value>  Number of processing threads you'd like to run (best for sim) (default: 1)
    --learns=<value>  Number of times to 'learn' the neural network with past data (default: 2)

noop
  description:
    Just do nothing. Can be used to e.g. generate candlesticks for training the genetic forex strategy.
  options:
    --period=<value>  period length, same as --period_length (default: 30m)
    --period_length=<value>  period length, same as --period (default: 30m)

rsi
  description:
    Attempts to buy low and sell high by tracking RSI high-water readings.
  options:
    --period=<value>  period length, same as --period_length (default: 2m)
    --period_length=<value>  period length, same as --period (default: 2m)
    --min_periods=<value>  min. number of history periods (default: 52)
    --rsi_periods=<value>  number of RSI periods
    --oversold_rsi=<value>  buy when RSI reaches or drops below this value (default: 30)
    --overbought_rsi=<value>  sell when RSI reaches or goes above this value (default: 82)
    --rsi_recover=<value>  allow RSI to recover this many points before buying (default: 3)
    --rsi_drop=<value>  allow RSI to fall this many points before selling (default: 0)
    --rsi_divisor=<value>  sell when RSI reaches high-water reading divided by this value (default: 2)

sar
  description:
    Parabolic SAR
  options:
    --period=<value>  period length, same as --period_length (default: 2m)
    --period_length=<value>  period length, same as --period (default: 2m)
    --min_periods=<value>  min. number of history periods (default: 52)
    --sar_af=<value>  acceleration factor for parabolic SAR (default: 0.015)
    --sar_max_af=<value>  max acceleration factor for parabolic SAR (default: 0.3)

speed
  description:
    Trade when % change from last two 1m periods is higher than average.
  options:
    --period=<value>  period length, same as --period_length (default: 1m)
    --period_length=<value>  period length, same as --period (default: 1m)
    --min_periods=<value>  min. number of history periods (default: 3000)
    --baseline_periods=<value>  lookback periods for volatility baseline (default: 3000)
    --trigger_factor=<value>  multiply with volatility baseline EMA to get trigger value (default: 1.6)

srsi_macd
  description:
    Stochastic MACD Strategy
  options:
    --period=<value>  period length, same as --period_length (default: 30m)
    --period_length=<value>  period length, same as --period (default: 30m)
    --min_periods=<value>  min. number of history periods (default: 200)
    --rsi_periods=<value>  number of RSI periods
    --srsi_periods=<value>  number of RSI periods (default: 9)
    --srsi_k=<value>  %D line (default: 5)
    --srsi_d=<value>  %D line (default: 3)
    --oversold_rsi=<value>  buy when RSI reaches or drops below this value (default: 20)
    --overbought_rsi=<value>  sell when RSI reaches or goes above this value (default: 80)
    --ema_short_period=<value>  number of periods for the shorter EMA (default: 24)
    --ema_long_period=<value>  number of periods for the longer EMA (default: 200)
    --signal_period=<value>  number of periods for the signal EMA (default: 9)
    --up_trend_threshold=<value>  threshold to trigger a buy signal (default: 0)
    --down_trend_threshold=<value>  threshold to trigger a sold signal (default: 0)

stddev
  description:
    Buy when standard deviation and mean increase, sell on mean decrease.
  options:
    --period=<value>  period length, set poll trades to 100ms, poll order 1000ms. Same as --period_length (default: 100ms)
    --period_length=<value>  period length, set poll trades to 100ms, poll order 1000ms. Same as --period (default: 100ms)
    --trendtrades_1=<value>  Trades for array 1 to be subtracted stddev and mean from (default: 5)
    --trendtrades_2=<value>  Trades for array 2 to be calculated stddev and mean from (default: 53)
    --min_periods=<value>  min_periods (default: 1250)

ta_ema
  description:
    Buy when (EMA - last(EMA) > 0) and sell when (EMA - last(EMA) < 0). Optional buy on low RSI.
  options:
    --period=<value>  period length, same as --period_length (default: 10m)
    --period_length=<value>  period length, same as --period (default: 10m)
    --min_periods=<value>  min. number of history periods (default: 52)
    --trend_ema=<value>  number of periods for trend EMA (default: 20)
    --neutral_rate=<value>  avoid trades if abs(trend_ema) under this float (0 to disable, "auto" for a variable filter) (default: 0.06)
    --oversold_rsi_periods=<value>  number of periods for oversold RSI (default: 20)
    --oversold_rsi=<value>  buy when RSI reaches this value (default: 30)

ta_macd
  description:
    Buy when (MACD - Signal > 0) and sell when (MACD - Signal < 0).
  options:
    --period=<value>  period length, same as --period_length (default: 1h)
    --period_length=<value>  period length, same as --period (default: 1h)
    --min_periods=<value>  min. number of history periods (default: 52)
    --ema_short_period=<value>  number of periods for the shorter EMA (default: 12)
    --ema_long_period=<value>  number of periods for the longer EMA (default: 26)
    --signal_period=<value>  number of periods for the signal EMA (default: 9)
    --up_trend_threshold=<value>  threshold to trigger a buy signal (default: 0)
    --down_trend_threshold=<value>  threshold to trigger a sold signal (default: 0)
    --overbought_rsi_periods=<value>  number of periods for overbought RSI (default: 25)
    --overbought_rsi=<value>  sold when RSI exceeds this value (default: 70)

trend_ema (default)
  description:
    Buy when (EMA - last(EMA) > 0) and sell when (EMA - last(EMA) < 0). Optional buy on low RSI.
  options:
    --period=<value>  period length, same as --period_length (default: 2m)
    --period_length=<value>  period length, same as --period (default: 2m)
    --min_periods=<value>  min. number of history periods (default: 52)
    --trend_ema=<value>  number of periods for trend EMA (default: 26)
    --neutral_rate=<value>  avoid trades if abs(trend_ema) under this float (0 to disable, "auto" for a variable filter) (default: auto)
    --oversold_rsi_periods=<value>  number of periods for oversold RSI (default: 14)
    --oversold_rsi=<value>  buy when RSI reaches this value (default: 10)

trendline
  description:
    Calculate a trendline and trade when trend is positive vs negative.
  options:
    --period=<value>  period length (default: 30s)
    --period_length=<value>  period length (default: 30s)
    --lastpoints=<value>  Number of trades for short trend average (default: 100)
    --avgpoints=<value>  Number of trades for long trend average (default: 1000)
    --lastpoints2=<value>  Number of trades for short trend average (default: 10)
    --avgpoints2=<value>  Number of trades for long trend average (default: 100)
    --min_periods=<value>  Basically avgpoints + a BUNCH of more preroll periods for anything less than 5s period (default: 15000)
    --markup_sell_pct=<value>  test (default: 0)
    --markdown_buy_pct=<value>  test (default: 0)

trust_distrust
  description:
    Sell when price higher than $sell_min% and highest point - $sell_threshold% is reached. Buy when lowest price point + $buy_threshold% reached.
  options:
    --period=<value>  period length, same as --period_length (default: 30m)
    --period_length=<value>  period length, same as --period (default: 30m)
    --min_periods=<value>  min. number of history periods (default: 52)
    --sell_threshold=<value>  sell when the top drops at least below this percentage (default: 2)
    --sell_threshold_max=<value>  sell when the top drops lower than this max, regardless of sell_min (panic sell, 0 to disable) (default: 0)
    --sell_min=<value>  do not act on anything unless the price is this percentage above the original price (default: 1)
    --buy_threshold=<value>  buy when the bottom increased at least above this percentage (default: 2)
    --buy_threshold_max=<value>  wait for multiple buy signals before buying (kill whipsaw, 0 to disable) (default: 0)
    --greed=<value>  sell if we reach this much profit (0 to be greedy and either win or lose) (default: 0)
```

## Interactive controls

While the `trade` command is running, Zenbot will respond to these keypress commands:

- Pressing `b` will trigger a buy, `s` for sell, and `B` and `S` for market (taker) orders.
- Pressing `c` or `C` will cancel any active orders.
- Pressing `m` or `M` will toggle manual mode (`--manual`)

These commands can be used to override what the bot is doing. Or, while running with the `--manual` flag, this allows you to make all the trade decisions yourself.

### noop strategy

If you want to use the bot without it trading for you, but just use it for the balance overview and manual trades, you can start the bot with `--strategy noop`, the bot will not trade automatically.

## Conf/argument override files

To run `trade` or `sim` commands with a pre-defined set of options, use:

```
zenbot trade --conf <path>
```

Where `<path>` points to a JS file that exports an object hash that overrides any conf or argument variables. For example, this file will run gdax.ETH-USD with options specific for that market:

```
var c = module.exports = {}

// ETH settings (note: this is just an example, not necessarily recommended)
c.selector = 'gdax.ETH-USD'
c.period = '10m'
c.trend_ema = 20
c.neutral_rate = 0.1
c.oversold_rsi_periods = 20
c.max_slippage_pct = 10
c.order_adjust_time = 10000
```

## GUI

A basic web UI is available at the url stated during startup.  This port can be configured in the conf.js or randomly assigned.
In it's infancy, there are a few caveats with the current UI.
- In order to have statistics displayed, they must first be dumped from the CLI.  Pressing `D` will refresh the statistics on each refresh of the dashboard.
- Currently the data is mostly static with the exception of the tradingview charts.
- Currently only READ-ONLY

## Reading the console output

![console](https://rawgit.com/deviavir/zenbot/master/assets/console.png)

From left to right:

- Timestamp in local time (grey, blue when showing "live" stats)
- Asset price in currency (yellow)
- Percent change of price since last period (red/green)
- Volume in asset since last period (grey)
- [RSI](http://stockcharts.com/school/doku.php?id=chart_school:technical_indicators:relative_strength_index_rsi) ANSI graph (red/green)
- `trend_ema_rate` (red/green, explained below)
- Current signal or action, including `buy`, `sell`, `buying`, `selling`, `bought`, `sold` and `last_trade_worth` (percent change in the trend direction since last buy/sell)
- Account balance (asset)
- Account balance (currency)
- Profit or loss percent (can be reset with `--reset_profit`)
- Gain or loss vs. buy/hold strategy

## Strategies

### The `trend_ema` strategy (default)

- The default strategy is called `trend_ema` and resides at `./extensions/strategies/trend_ema`.
- Defaults to using a 2m period, but you can override this with adding e.g. `--period=5m` to the `sim` or `trade` commands.
- Computes the 26-period EMA of the current price, and calculates the percent change from the last period's EMA to get the `trend_ema_rate`
- Considers `trend_ema_rate >= 0` an upwards trend and `trend_ema_rate < 0` a downwards trend
- Filters out low values (whipsaws) by `neutral_rate`, which when set to `auto`, uses the standard deviation of the `trend_ema_rate` as a variable noise filter.
- Buys at the beginning of upwards trend, sells at the beginning of downwards trend
- If `oversold_rsi` is set, tries to buy when the RSI dips below that value, and then starts to recover (a counterpart to `--profit_stop_enable_pct`, which sells when a percent of profit is reached, and then dips)
- The bot will always try to avoid trade fees, by using post-only orders and thus being a market "maker" instead of a "taker". Some exchanges will, however, not offer maker discounts.

### The `macd` strategy

The moving average convergence divergence calculation is a lagging indicator, used to follow trends.

- Can be very effective for trading periods of 1h, with a shorter period like 15m it seems too erratic and the Moving Averages are kind of lost.
- It's not firing multiple 'buy' or 'sold' signals, only one per trend, which seems to lead to a better quality trading scheme.
- Especially when the bot will enter in the middle of a trend, it avoids buying unless it's the beginning of the trend.

### The `rsi` strategy

Attempts to buy low and sell high by tracking RSI high-water readings.

- Effective in sideways markets or markets that tend to recover after price drops.
- Risky to use in bear markets, since the algorithm depends on price recovery.
- If the other strategies are losing you money, this strategy may perform better, since it basically "reverses the signals" and anticipates a reversal instead of expecting the trend to continue.

### The `sar` strategy

Uses a [Parabolic SAR](http://stockcharts.com/school/doku.php?id=chart_school:technical_indicators:parabolic_sar) indicator to trade when SAR trend reverses.

- Tends to generate earlier signals than EMA-based strategies, resulting in better capture of highs and lows, and better protection against quick price drops.
- Does not perform well in sideways (non-trending) markets, generating more whipsaws than EMA-based strategies.
- Most effective with short period (default is 2m), which means it generates 50-100 trades/day, so only usable on GDAX (with 0% maker fee) at the moment.
- Tested live, [results here](https://github.com/carlos8f/zenbot/pull/246#issuecomment-307528347)

### The `speed` strategy

Trade when % change from last two 1m periods is higher than average.

**This strategy is experimental and has WILDLY varying sim results. NOT RECOMMENDED YET.**

- Like the sar strategy, this generates early signals and can be effective in volatile markets and for sudden price drop protection.
- Its weakness is that it performs very poorly in low-volatility situations and misses signals from gradually developing trends.

### Tips for tweaking options

- Trade frequency is adjusted with a combination of `--period` and `--trend_ema`. For example, if you want more frequent trading, try `--period=5m` or `--trend_ema=15` or both. If you get too many ping-pong trades or losses from fees, try increasing `period` or `trend_ema` or increasing `neutral_rate`.
- Sometimes it's tempting to tell the bot trade very often. Try to resist this urge, and go for quality over quantity, since each trade comes with a decent amount of slippage and whipsaw risk.
- `--oversold_rsi=<rsi>` will try to buy when the price dives. This is one of the ways to get profit above buy/hold, but setting it too high might result in a loss if the price continues to fall.
- In a market with predictable price surges and corrections, `--profit_stop_enable_pct=10` will try to sell when the last buy hits 10% profit and then drops to 9% (the drop % is set with `--profit_stop_pct`). However in strong, long uptrends this option may end up causing a sell too early.
- For Kraken and GDAX you may wish to use `--order_type="taker"`, this uses market orders instead of limit orders. You usually pay a higher fee, but you can be sure that your order is filled instantly. This means that the sim will more closely match your live trading. Please note that GDAX does not charge maker fees (limit orders), so you will need to choose between not paying fees and running the risk orders do not get filled on time, or paying somewhat high % of fees and making sure your orders are always filled on time.

## Notifiers

Zenbot employs various notifiers to keep you up to date on the bot's actions. We currently send a notification on a buy and on a sell signal.

### pushbullet

Supply zenbot with your api key and device ID and we will send your notifications to your device.
https://www.pushbullet.com/

### Slack

Supply zenbot with a webhook URI and zenbot will push notifications to your webhook.
https://slack.com/

### XMPP

Supply zenbot with your XMPP credentials and zenbot will send notifications by connecting to your XMPP, sending the notification, and disconnecting.
https://xmpp.org/

### IFTTT

Supply zenbot with your IFTTT maker key and zenbot will push notifications to your IFTTT.
https://ifttt.com/maker_webhooks

### DISCORD

Supply zenbot with your Discord webhook id and webhook token zenbot will push notifications to your Discord channel.

How to add a webhook to a Discord channel
https://support.discordapp.com/hc/en-us/articles/228383668

### Prowl

Supply zenbot with your Prowl API key and zenbot will push notifications to your Prowl enabled devices.
https://www.prowlapp.com/

### TextBelt

Supply zenbot with your TextBelt API key and zenbot will send SMS notifications to your cell phone.
https://www.textbelt.com/

## Rest API

You can enable a Rest API for Zenbot by enabling the following configuration
```
c.output.api = {}
c.output.api.on = true
c.output.api.port = 0 // 0 = random port
```
You can choose a port, or pick 0 for a random port.

Once you did that, you can call the API on: http://\<hostname\>:\<port\>/trades

## Manual trade tools

Zenbot's order execution engine can also be used for manual trades. Benefits include:

- Avoids market-order fees by using a short-term limit order
- Can automatically determine order size from account balance
- Adjusts order every 30s (if needed) to ensure quick execution
- If an order is partially filled, attempts to re-order with remaining size

The command to buy is:

```
zenbot buy <selector> [--size=<size>] [--pct=<pct>]
```

For example, to use your remaining USD balance in GDAX to buy Bitcoin:

```
zenbot buy gdax.BTC-USD
```

Or to sell 10% of your BTC,

```
zenbot sell gdax.BTC-USD --pct=10
```

## Chat with other Zenbot users

[![zenbot logo](https://rawgit.com/deviavir/zenbot/master/assets/discord.png)](https://discord.gg/ZdAd2gP)

Zenbot has a Discord chat! You can get in [through this invite link](https://discord.gg/ZdAd2gP).

## Donate

P.S., some have asked for how to donate to Zenbot development. We accept donations at **Bitcoin addresses** below:

### carlos8f's BTC (original zenbot author)

`187rmNSkSvehgcKpBunre6a5wA5hQQop6W`

### DeviaVir's BTC (current maintainer)

`3BZojxm9q8uGWvvsudLCmqfBhtT7ceeSQk`

![zenbot logo](https://rawgit.com/deviavir/zenbot/master/assets/zenbot_square.png)

Thanks!

- - -

### License: MIT

- Copyright (C) 2018 Carlos Rodriguez
- Copyright (C) 2018 Terra Eclipse, Inc. (http://www.terraeclipse.com/)

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the &quot;Software&quot;), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is furnished
to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED &quot;AS IS&quot;, WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

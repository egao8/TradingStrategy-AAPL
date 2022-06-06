## Introduction

Leveraging a strategy coined the [Dual Moving Average Crossover (DMAC)](https://faculty.fuqua.duke.edu/~charvey/Teaching/BA453_2002/CCAM/CCAM.htm#:~:text=In%20the%20dual%20moving%20average,of%20thought%3A%20Technical%20and%20Value./), the following is a stock trading strategy that prompts decisions for when to buy and sell a stock. With AAPL data over the span of five years, the strategy aims to calculate two moving averages of case exchange rates of Apple stock, determine the crossover points, and ultimately output a decision on when to sell and buy.

## File Structure

 - AAPL.csv is used to train the strategy in order for datasets to be
   manipulated.

## Examples

![Raw Data of AAPL stock price](https://pasteboard.co/MFf9eI5CPfTf.png)
![Visualisation of Data](https://pasteboard.co/fnOikmVQQBRY.png)

## Buy or Sell Algorithm

  

      def buy_sell(data):
	      sigPriceBuy = []
	      sigPriceSell = []
	    
	      flag = -1
	    
	      for i in range(len(data)):
	        if data["SMA30"][i] > data["SMA100"][i]:
	          if flag != 1:
	            sigPriceBuy.append(data["AAPL"][i])
	            sigPriceSell.append(np.nan)
	            flag = 1
	          else:
	            sigPriceBuy.append(np.nan)
	            sigPriceSell.append(np.nan)
	        elif data["SMA30"][i] < data["SMA100"][i]:
	          if flag != 0:
	            sigPriceBuy.append(np.nan)
	            sigPriceSell.append(data["AAPL"][i])
	            flag = 0
	          else:
	            sigPriceBuy.append(np.nan)
	            sigPriceSell.append(np.nan)
	        else:
	          sigPriceBuy.append(np.nan)
	          sigPriceSell.append(np.nan)
	    
	      return (sigPriceBuy, sigPriceSell)


# crypto-NN

###		Quite recently, Cryptocurrencies have become a hot topic for financial consideration.
#	For all intents and purposes, they behave like stocks, as traders carefully anticipate the rise 
#	and fall of the closing price for their cryptocurrency of choice. I wanted to see if there was
#	a way to utilize deep learning, specially implementing long short-term-memory design, to predict the 
	overall trends in the rise and fall of various cryptocurrencies.
		The Network itself is implemented using Keras and Tensorflow frameworks, two open-source deep 
	learning libraries. It derives its data from that which is available on the Yahoo! finance database. 
	That data is preprocessed using pandas, another open source library, to modify it such that 
	it will interact with Keras’ LSTM model. We want to upload the fourth column (which corresponded to 
	crypto closing prices) to a pandas dataframe. Further information about the data preprocessing
	is explained in the following paragraph about the structure of the neural network itself.
		Long short-term-memory (LSTM) neural networks are a specialized implementation of recurrent 
	neural networks. They use some specified number of previous data values to predict a future value. 
	This range of values is referred to as a window. Thusly, we must partition our training data into 
	these windows as a part of our data pre-processing. In this case, we have split 
	the data into 2 sets, trainX and trainY. These data-arrays contain the same values (except at their edges),
	but the indices are off by one, allowing the network access to the both past and future values
	simultaneously. Finally, the model itself utilizes mean squared error as its loss function, 
	as it is one of the most popular choices for quantitative predictions.
		As this network is still a work in progress, the accuracy rates are quite low. However, the 
	model did quite well in predicting the overall shape of the crypto market, which is useful in 
	predicting the long-term trends of the closing values. The inherent problem with predicting crypto-prices 
	lies in relative novelty of cryptocurrencies as a whole, as even the oldest crypto coins have 
	only been around for around seven years.
		In order to use the model, the user must upload a CSV file downloaded from the Yahoo! finance server. 
	Pandas is set to read the column that contains the closing price for the intended cryptocurrency, 
	so the user has some freedom in which currency on which to train the network. When the code 
	executes the file = files.upload() line, it will prompt the user to select a file to upload. 
	From there, they must fill in the line data_btc = pd.read_csv(“FILE_NAME", usecols=[4]) with 
	the appropriate CSV filename. After that, they should be able to train the network on the 
	currency of their choice.

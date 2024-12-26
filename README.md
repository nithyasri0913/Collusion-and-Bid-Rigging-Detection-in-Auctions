# Collusion and Bid-Rigging Detection in Auctions

This project implements a system for detecting potential collusion and bid-rigging activities in auction data using a combination of DBSCAN clustering and statistical anomaly detection techniques. The system identifies suspicious bidders by analyzing their bidding patterns, such as frequent bids, unusually short time gaps between consecutive bids, price deviations, and statistical outliers in their bidding behavior.

## Key Components
### 1. DBSCAN Clustering
DBSCAN is an unsupervised machine learning algorithm that identifies clusters of similar data points and flags outliers as noise (denoted by -1).
This project uses DBSCAN to group bidders exhibiting similar bidding behavior and identifies those that deviate significantly as outliers.
### 2. Z-Score for Statistical Anomaly Detection
The Z-Score is used to identify how far a bidder’s bid deviates from the mean of the bids.
Bidders with a Z-Score greater than 3 or less than -3 are flagged as potential outliers.
### 3. Price Deviation Analysis
Price deviations between the auction’s starting bid and the final price are calculated to identify if any bidder is consistently pushing the price higher than expected.
The threshold for price deviation is determined based on the 95th percentile of price deviation values.
### 4. Bidder Behavior Analysis
Frequency of bids placed by each bidder is calculated.
The time gap between consecutive bids is tracked to detect suspicious behavior, such as placing multiple bids within a very short time frame.
### 5. Collusion and Bid-Rigging Detection Logic
The system combines DBSCAN clusters, statistical outlier detection (Z-Score), price deviation analysis, and bidder behavior patterns to detect potential collusion or bid-rigging activities.

## Key Variables and Thresholds
### DBSCAN Parameters:
#### 1. eps: Maximum distance between two points for them to be considered as part of the same cluster (set to 0.5 in the example).
#### 2. min_samples: Minimum number of samples required in a neighborhood to form a cluster (set to 5 in the example).
### Z-Score Threshold:
Bidders with a Z-score above 3 or below -3 are considered outliers (flagged as suspicious).
### Price Deviation Threshold: 
Set at the 95th percentile of price deviations to detect bidders pushing the price significantly higher than the starting bid.

## Results and Output
The output of the system will be a list of potential colluding or suspicious bidders, including relevant features such as:
bidder: The ID of the suspicious bidder.
auctionid: The ID of the auction.
bid: The amount bid by the bidder.
bid_zscore: The Z-score of the bid.
dbscan_cluster: The DBSCAN cluster label (clusters other than -1 are considered).

## Future Work
Long-Term Behavioral Patterns: This logic can be extended to track behavior across multiple auctions and detect long-term collusion.
Further Customization: The thresholds and parameters used for DBSCAN, Z-Score, and other statistical methods can be further customized based on the specific characteristics of the auction data.
Advanced Machine Learning Techniques: Integrating more advanced anomaly detection techniques such as Isolation Forests or One-Class SVMs could improve the detection of bid-rigging and collusion.

## Conclusion
This project provides a foundation for detecting suspicious bidding behavior using clustering and statistical techniques. By applying DBSCAN clustering and statistical anomaly detection, we can identify potential collusion or bid-rigging activities and make auctions more transparent and fair.

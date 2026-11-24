# Experiment 6 : Sentiment Analysis of Product Reviews Using TextBlob

## Aim
To load product review text, perform sentiment polarity analysis using the `TextBlob` library, classify reviews into **Positive**, **Negative**, or **Neutral** categories, and visualize the overall sentiment distribution using a Matplotlib bar chart.

## Algorithm

1. **Start** the program.
2. **Import Libraries**: Import `TextBlob` from the `textblob` package for Natural Language Processing (NLP) sentiment analysis and `matplotlib.pyplot` as `plt` for bar chart visualization.
3. **Create Review Dataset**: Define a Python list `reviews` containing 10 sample customer product review strings.
4. **Initialize Sentiment Counters**: Set `positive = 0`, `negative = 0`, and `neutral = 0` to track category counts.
5. **Analyze & Classify Each Review**:
   * Iterate through each `review` in `reviews`.
   * Create a `TextBlob(review)` object and extract `polarity = analysis.sentiment.polarity`.
   * Classify the review:
     * If $\text{polarity} > 0.1$, label as `"Positive"` and increment `positive`.
     * Else if $\text{polarity} < -0.1$, label as `"Negative"` and increment `negative`.
     * Else, label as `"Neutral"` and increment `neutral`.
   * Display the review text, rounded polarity score, and assigned sentiment label.
6. **Display Summary Counts**: Print the total count of Positive, Negative, and Neutral reviews.
7. **Visualize Sentiment Distribution**:
   * Plot a bar chart using `plt.bar()` with sentiment categories on the X-axis and review counts on the Y-axis.
   * Add a title, axis labels, and render the chart via `plt.show()`.
8. **Stop** the program.

## Functions and Methods Used

| Category | Function / Attribute | Purpose / Description |
| :--- | :--- | :--- |
| **Sentiment Analysis** | `TextBlob(text)` | Wraps a text string in a TextBlob NLP object for linguistic analysis |
| | `.sentiment.polarity` | Computes a floating-point sentiment polarity score in the range $[-1.0, +1.0]$ |
| **Formatting & Math** | `round(polarity, 2)` | Rounds raw polarity scores to 2 decimal places for clean console output |
| **Visualization (Matplotlib)** | `plt.figure()`, `plt.bar()` | Initializes a figure window and renders a color-coded vertical bar chart |
| | `plt.title()`, `plt.xlabel()`, `plt.ylabel()`, `plt.show()` | Configures chart title, axis labels, and displays the final visualization |

## Program

# Sentiment Analysis on Product Reviews using TextBlob  

from textblob import TextBlob  
import matplotlib.pyplot as plt  

# Step 1: Create a list of sample product reviews  
reviews = [  
    "The product is excellent and works perfectly. I love it.",  
    "Great quality and fast delivery. Very happy with this purchase.",  
    "This is an amazing product and I highly recommend it.",  
    "Good value for money and easy to use.",  
    "I am satisfied with the product. It is useful.",  
    "The product is okay and does what it says.",  
    "The item is average, nothing special.",  
    "The product is disappointing and poor quality.",  
    "Terrible experience. The product stopped working quickly.",  
    "I hate this product. It is waste of money."  
]  

# Step 2: Initialize sentiment counters  
positive = 0  
negative = 0  
neutral = 0  

print("PRODUCT REVIEW SENTIMENT ANALYSIS")  
print("----------------------------------")  

# Step 3: Analyze sentiment for each review  
for review in reviews:  

    analysis = TextBlob(review)  
    polarity = analysis.sentiment.polarity  

    if polarity > 0.1:  
        sentiment = "Positive"  
        positive += 1  

    elif polarity < -0.1:  
        sentiment = "Negative"  
        negative += 1  

    else:  
        sentiment = "Neutral"  
        neutral += 1  

    print("\nReview:", review)  
    print("Polarity:", round(polarity, 2))  
    print("Sentiment:", sentiment)  

# Step 4: Display summary  
print("\n----- SENTIMENT SUMMARY -----")  
print("Total Reviews:", len(reviews))  
print("Positive Reviews:", positive)  
print("Negative Reviews:", negative)  
print("Neutral Reviews:", neutral)  

# Step 5: Plot sentiment distribution  
categories = ["Positive", "Negative", "Neutral"]  
counts = [positive, negative, neutral]  

plt.figure(figsize=(8, 5))  

plt.bar(categories, counts,  
        color=["green", "red", "orange"])  

plt.title("Product Review Sentiment Distribution")  
plt.xlabel("Sentiment Categories")  
plt.ylabel("Number of Reviews")  

plt.grid(axis="y", linestyle="--", alpha=0.5)  

plt.show()  
## Output
Original Customer Feedback:  
The products are good, and customers love the fast delivery.  
However, the packages were delayed.  

Tokenized Words:  
['The', 'products', 'are', 'good', ',', 'and',  
 'customers', 'love', 'the', 'fast', 'delivery',  
 '.', 'However', ',', 'the', 'packages', 'were',  
 'delayed', '.']  

After Stopword Removal and Punctuation Filtering:  
['products', 'good', 'customers', 'love', 'fast',  
 'delivery', 'packages', 'delayed']  

Final Lemmatized Words:  
['product', 'good', 'customer', 'love', 'fast',  
 'delivery', 'package', 'delayed']  
<img width="791" height="527" alt="WhatsApp Image 2026-11-24 at 21 55 59" src="https://github.com/user-attachments/assets/27a8a208-6cc5-449b-82fa-cb0bea636da7" />


## Result
The program successfully loads a list of sample product reviews, applies `TextBlob` sentiment polarity scoring to classify each review's emotional tone, prints summary counts, and visualizes the overall distribution with a Matplotlib bar chart.


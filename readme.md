**Introduction**


In our daily encounters with online news outlets, the information usually has already been classified into categories (such as that of politics, travel, entertainment, etc.) for our convenience. But this is only a recent invention. As a historian, this author is curious about how to process historical text so we can gain insight into long-term patterns. This project will train a model to classify historical news into categories based on annotated data and, from there, try to explore if any interesting patterns emerge. 
Newspapers have long been a primary source for historians due to their easy accessibility, wide coverage, and large quantities. It is essentially a snapshot of the past. But the sheer quantity also poses a problem for historians whose only toolkit for data processing is close reading, namely, to carefully interpret the nuances and details of a few selected texts. The obvious shortcoming is that historians would often overlook the long-term patterns and macro structures. Digital methods provide the possibilities of distant reading, a term first coined by Moretti (2000), which means applying digital methods to discern patterns in a large corpus. However, the methods used are usually simple rule-based string matching and searching. For instance, Moretti (2013) counts the length of titles of British novels published from 1740 to 1850 and discovers the titles have progressed from being extremely long to gradually shorter and to the present length that we are familiar with. The reason he gives was the rise of book reviews and mass media as readers no longer needed to rely on a long and detailed title for choosing a book. String operation is simple and efficient, but it also limits the possibility of exploring more complex patterns in the text. Machine learning, on the other hand, provides a more flexible and promising tool for distant reading.
This project aims to explore the application of Machine Learning models in historical interpretation. People’s Daily is a premier national newspaper in China and the official newspaper of the ruling party since 1948. Its news coverage reflects not only the editors ‘or readers’ preference but also political decisions on the high level, and therefore exerts wide influence in society. Scholars often use its new report as indicators for new trends in policy or public discourses (for a few representatives, see Fan, Xue & Xu 2018; Zeng, Chan & Schafer 2020). This project will train a model to classify People’s Daily’s news reports by content. The ultimate purpose is to examine if there was any long-term change in the relative propositions of categories and to explore what were the structural reasons behind the trends.


**Data**


The targeted historical data is the full-texted People’s Daily corpus from 1946 to 2003(People’s Daily Digital Text). The training data come from an annotated dataset for news classification, the Categorized News Dataset from Fudan University, downloaded from Kaggle (Fudan University’s Natural Language Processing Group, 2018). It has almost 20,000 paragraphs of Chinese text, classified into 20 categories, including history, art, military, politics, etc. A quick look reveals that most annotated texts were drawn from news reports or journal articles in 1996. The author is aware that the training data could be substantially different from some text in the People’s Daily corpus; hence the model trained on the news from 1996 would probably perform poorly on texts generated in the 1940s. The limits will be discussed in the end.

**Research Design**


This research goes in the following steps. The first is data pre-processing. Because of the nature of the Chinese language, there is no space between each word. Sentences are just a consecutive string of Chinese characters. Depending on the semantic context, a Chinese character can independently connote meaning or, together with its previous or next characters, form a word denoting distinct meaning. Therefore, the bulk of data preprocessing is to segment all the Chinese texts into words separated with a blank space. There are several Chinese-segmentation python packages available. This study uses the LAC (Jiao, Sun & Sun 2018). In the attendant Jupyter notebook file, the function processing_directory written by the author will implement the segmentation process. It will output segmented Chinese documents and their corresponding classification tags.
The second step is to employ the Naïve Bayes model to train and test the model. The features are segmented Chinese words. Finally, the model will be applied to the targeted data, the People’s Daily corpus, for an assessment. The assessment entails manually evaluating whether the machine-predicted label correctly reflects the content of the document in question. However, the Chinese segmenting process on the whole newspaper corpus requires a large amount of computational power, which is beyond the scope of a class paper. And the human interpretation of text content for a large corpus is also time-consuming. The author instead selected only a small subset of the People’s Daily text to estimate the external validity of the model. As a result, 60 news reports randomly selected from January 1963 and October 1990, with 30 pieces from each month, constitute the assessment data. The expectation is that the model’s accuracy on the 1990 data would be higher because the ways news was composed in 1996(the time when training data were generated) should be more similar to 1990 than 1963.



**Results**


Table 1 shows the model metrics on test data (The test data included in the Fudan dataset, not the People’s Daily data). There are 20 categories in total, and the weighted average precision is 0.82. Overall, this is not bad. But some categories’ accuracy is extremely low, approximating to 0. This could be attributed to the small sample size. Each of the 11 categories, including Communication, Education, Electronics, Energy, Mine, Military, Transport, et al., has less than 100 samples. This is also true for the training data, a feature of the Fudan dataset the author had missed out. On the other hand, the model performed well for categories with more than 400 samples, including Agriculture (0.86), Art(0.79), Computer(0.93), and Economy(0.82).
Moving on to the assessment data (People Daily data), The model performs surprisingly better on the 1963 data than on the 1990 data. Despite that, in theory, the latter should be more similar in nature to the training data. The precision and recall are 0.82 and 0.73 for the 1963 data (Table 2) and 0.76 and 0.67 for the 1990 data (Table 3). One possible explanation is that the model generally performs well regarding some categories; for example, the 'Politics' takes up a relatively high proportion in the 1963 data (60%, 18 samples) compared to a percentage of 36% (11 samples) in the 1990 data. Of course, this is a very tentative observation. The sample number (30) is still small.
Further statistic tests would tell the significance of the difference. But historical knowledge does inform us that Chinese society was over-politicized in the pre-1980 years. Explicitly political content should constitute a significantly higher portion of news in  People's Daily during this time than in the 1990s. Therefore, How the categories are distributed in the targeted data and training data would be a good point of departure for rethinking how to revise the model further.


**Limits**


Applying supervised machine learning to historical research faces several limits. The first is the scale and types of OCRed text are limited, particularly for non-English languages. Historians regularly deal with archives, memoirs, manuscripts, and personal letters. Newspaper is only one of many types of primary sources and not even the most widely used type. And yet, the OCRed newspaper text is still only a tiny fraction of the historical newspaper collections in libraries and archives, not to mention other types of primary sources.
Second, data labeling is often done based on concepts popular in daily lives at present, which stands less of a problem when the downstream tasks are also part of our daily lives. Take the category labeling used in this study, for example. The 20 categories fit well into our perception of contemporary events. But when applied to serious analysis of long-term data, the difference between categories such as agriculture and economics seems ambiguous and uninformative, for agriculture is still the backbone of many developing economies, not to mention the periods a few decades ago. Hence, it is essential to design conceptual frameworks of labeling corresponding to the downstream task. If machine learning is to be applied in historical research, historians would better be the ones who create and assign labels, or at least they need to review and adjust the training dataset seriously. 
Finally, historians and other humanities scholars will need to engage in the discussion of models and technologies, making their voices and insights heard in the science and technology community.


**References**


1.	Fudan University’s Natural Language Processing Group. 2018. Categorized News Dataset from Fudan University: Chinese news dataset of 20 different categories. Retrieved from https://www.kaggle.com/louislung/categorised- news-dataset-from-fudan-university/version/1 
2.	Fan, S., Xue, L., & Xu, J. (2018). What Drives Policy Attention to Climate Change in China? An Empirical Analysis through the Lens of People’s Daily. Sustainability, 10(9), 2977.
3.	Jiao, Zhenyu, Shuqi Sun, and Ke Sun. 2018 "Chinese lexical analysis with deep bi-gru-crf network." arXiv preprint arXiv:1807.01882. 
4.	Moretti, F. (2000). Conjectures on world literature. New left review, 1, 54.
5.	Moretti, F. (2013). Distant reading. Verso Books.
6.	People’s Daily Digital Text http://www.mzdbl.cn/rmrb/index.html.
7.	Zeng, J., Chan, C. H., & Schäfer, M. S. (2020). Contested Chinese dreams of AI? Public discourse about artificial intelligence on Wechat and People’s Daily Online. Information, Communication & Society, 1-22.

**Tables**

Table 1 Testing Metrics
<img title= "Table 1 Testing Metrics" src = /Testing_Metrics.png>


Table 2 1963 Data Metrics
<img title= "Table 2 1963 Data Metrics" src = /1963_Data_Metrics.png>


Table 3 1990 Data Metrics
<img title= "Table 3 1990 Data Metrics" src = /1990_Data_Metrics.png>

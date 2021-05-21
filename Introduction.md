Introduction
In our daily life, while browsing internet, news has already been classified into categories (such as politics, travel, entertainment and so forth) for our convenience. But it may not necessarily be so in the past. As a historian, the author is curious about how to process historical text so we can gain insight into long-term patterns. This project will train a model to classify historical news into categories based on annotated data and from there to explore if any interesting patterns emerge. 
Newspapers have long been a primary source for historians, due to their essay accessibility, wide-coverage, and large quantity. It is essentially a snapshot of the past. But the sheer quantity also poses a problem for historians whose only toolkit for data processing is close reading, namely, to carefully interpret the nuances and details of a few selected texts. The obvious shortcoming is that historians would often overlook the long-term patterns and macro structures. Digital tools provide the possibility of distant reading, a term first coined by a literary scholar, Moretti (2000). It means applying digital methods to discern patterns in a large corpus. However, the methods usually remain the simple rule-based string matching and searching. For instance, Moretti (2013) counts the length of titles of British novels published from 1740 to 1850, and discovers the titles had been extremely long, and gradually became shorter until to the present length that we are familiar with. The reason was the rise of book reviews and mass media, as readers had no longer needed to rely on a long and detailed title for choosing a book. String operation is simple and efficient, but it also limits the possibility of exploring more complex patterns in the text. Machine learning on the other hand provides more flexibility and seems a promising tool for distant reading.
This project aims to explore the application of Machine Learning models in historical interpretation. People’s Daily is a premier national newspaper in China, and the official newspaper of the ruling party since 1948. Its news coverage reflects not only the editors ‘or readers’ preference, but also political decisions on the high level, and therefore exerts wide influence in the society. Scholars often use its reports as indicators for new trends in policy or public discourses (for a few representatives, see Fan, Xue & Xu 2018; Zeng, Chan & Schafer 2020). This project will train a model to classify news on People’s Daily by content. The final purpose is to examine if there was any long-term change in the relative percentage of categories, and to explore what were the structural reasons behind the trends. 
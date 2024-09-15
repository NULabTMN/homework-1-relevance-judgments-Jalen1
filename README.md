[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/J7-Ztghw)
# CS6200 / IS4200: Relevance Judgments

TLDR: In this assignment, you will choose three topics represented in the _Chronicling America_ collection of historic newspapers and record the text of passages relevant to those topics in the file `topics.xml`.

As we discussed in class, the most common way to evaluate ad hoc information retrieval systems is to create *test collections*, as in the [Text Retrieval Conferences (TREC)](https://trec.nist.gov/) run by the US [National Institute of Standards and Technology](https://www.nist.gov/). These consist of a set of information needs, called *topics*. Each topic contains a brief query (the **title**) and longer natural language query (the **description**) and an even longer **narrative** that explains what the user was looking for an what kinds of information count as relevant or not for that information need.

Here is one example TREC topic:

| field | contents |
| ----- | -------- |
| title | pet therapy |
| description | How are pets or animals used in therapy for humans and what are the benefits? |
| narrative | Relevant documents must include details of how pet- or animal-assisted therapy is or has been used. Relevant details include information about pet therapy programs, desscriptions of the circumstances in which pet therapy is used, the benefits of this type of therapy, the degree of success of this therapy, and any laws or regulations governing it. |

After these topics are created, annotators feed the queries to search engines and create *relevance judgments* by looking through the results. The document identifiers of relevant and non-relevant results are appended to each topic.

In this assignment, you will go through the process of creating relevance judgments for an existing set of topics created by the Library of Congress for their [_Chronicling America_](https://chroniclingamerica.loc.gov/) project, which digitized millions of pages of historic newspapers. As part of this project, librarians have created &ldquo;Research Guides&rdquo; on a few hundred topics. Here is [an alphabetical list of these research guides](https://guides.loc.gov/chronicling-america-topics/alphabetical-order), which you can also view by date, library subject heading, and some other categories.

As an example, consider the research guide for the [bicycle craze in the years around 1900](https://guides.loc.gov/chronicling-america-bicycle-craze). In addition to the narrative and a timeline of events, you can click [&ldquo;Read more about it!&rdquo;](https://guides.loc.gov/chronicling-america-bicycle-craze/selected-articles) to see a list of suggested queries and a few example relevant documents. For most topics, these relevant documents are by no means exhaustive.

**Your task** is to choose **three research guides** and judge the relevance of search results to those topics.  This is made more complex than some evaluations because this is a **passage retrieval** task, i.e., only some of the text on each newspaper page may be relevant to the topic. For instance, [here is the first page listed for the Bicycle Craze topic](https://chroniclingamerica.loc.gov/lccn/sn85058130/1889-02-24/ed-1/seq-6/#words=bicycles+safety).  Only some of the second column is relevant. Your job, therefore, is to judge whether pages are relevant and, if so, what text on that page is relevant.

You should select relevant passages for all of the documents list on your topics' &ldquo;Read more about it!&rdquo; page. In addition, you should judge **ten additional** documents by constructing a query and searching *Chronicling America*.  For these ten, some of the results may be judged relevant and some non-relevant.  You will record your judgements in a simple XML file.  We have provided the skeleton structure in `topics.xml` for you to edit.  In `bicycle-example.xml`, we show what information you should record:
```xml
<topics>
  <topic>
    <id>https://guides.loc.gov/chronicling-america-bicycle-craze</id>
    <results>
      <result>
	<id>https://chroniclingamerica.loc.gov/lccn/sn85058130/1889-02-24/ed-1/seq-6/</id>
	<rel>1</rel>
	<text>THE WORLD ON WHEELS
The Improvements Made The
...
      </text>
      </result>
      <result>
	<id>https://chroniclingamerica.loc.gov/lccn/sn85058130/1889-03-17/ed-1/seq-11/</id>
	<rel>1</rel>
	<text>ASTRIDE THE WHEEL
Another Plea in Behalf of the
...
      </text>
    </result>
    <result>
      <id>https://chroniclingamerica.loc.gov/lccn/sn88085722/1891-07-01/ed-1/seq-2/</id>
      <rel>0</rel>
    </result>
  </results>
</topic>
</topics>
```

Each `<topic>` tag should contain an `<id>`, with the URL of the Research Guide, and a `<results>` tag with one or more `<result>` tags.  Each `<result>` contains:
* an `<id>` tag with the URL of the newspaper page,
* a `<rel>` tag containing 1 for relevant or 0 for non-relevant, and
* a `<text>` tag, if the document is relevant, containing the text of the relevant passage.

In recording page URLs, please remove the information after `#words=` used to highlight search terms.  To find the text of a newspaper page, click on the Text link just above the image.  For example, [here is the text of the first result for the Bicycle Craze topic](https://chroniclingamerica.loc.gov/lccn/sn85058130/1889-02-24/ed-1/seq-6/ocr/).  (Note that you could also construct this link by appending `/ocr` to the main URL for the newspaper page.) Select the text of the relevant passage and copy it into the `<text>` tag for the result.

Once you have added all this information for three topics to the `topics.xml` file, check in your changes and push them to GitHub.

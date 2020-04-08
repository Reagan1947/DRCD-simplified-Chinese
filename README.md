# DRCD Simplified Chinese 
> This is simplified Chinese version of DRCD SQuAD1.0 Dataset. 
> 这是简体中文版的DRCD的SQuAD1.0数据集

​	台达阅读理解资料集 Delta Reading Comprehension Dataset (DRCD) 属于通用领域繁体中文机器阅读理解资料集。
​	本资料集期望成为适用于迁移学习之标准中文阅读理解资料集。
​	本资料集从2,108篇维基条目中整理出10,014篇段落，并从段落中标注出30,000多个问题

​	关于资料集之更详细资讯请洽询论文：
​	For more information please refer to Paper https://arxiv.org/abs/1806.00920

## Data format 数据格式

- version : <String> 资料集版本
- data : <Array>
  - title : <String> : 文章标题
  - id : <String> : 文章编号
  - paragraphs : <Array>
    - id : <String> : 文章编号_段落编号
    - context : <String> : 段落内容
    - qas : <Array>
      - question : <String> : 问题内容
      - id :<String> : 文章编号_段落编号_问题编号
      - answers : <Arrays>
        - answer_start : <int> text在文中位置
        - id : <String> : "1"表示为人工标注的答案，"2"以上为人工答题的答案
        - text : <string> : 答案内容

## Example 数据举例：

  ```json
{
  "version": "1.3",
  "data": [
    {
      "title": "基督新教",
      "id": "2128",
      "paragraphs": [
        {
          "context": "基督新教與天主教均繼承普世教會歷史上許多傳統教義，如三位一體、聖經作為上帝的啟示、原罪、認罪、最後審判等等，但有別於天主教和東正教，新教在行政上沒有單一組織架構或領導，而且在教義上強調因信稱義、信徒皆祭司， 以聖經作為最高權威，亦因此否定以教宗為首的聖統制、拒絕天主教教條中關於聖傳與聖經具同等地位的教導。新教各宗派間教義不盡相同，但一致認同五個唯獨：唯獨恩典：人的靈魂得拯救唯獨是神的恩典，是上帝送給人的禮物。唯獨信心：人唯獨藉信心接受神的赦罪、拯救。唯獨基督：作為人類的代罪羔羊，耶穌基督是人與上帝之間唯一的調解者。唯獨聖經：唯有聖經是信仰的終極權威。唯獨上帝的榮耀：唯獨上帝配得讚美、榮耀",
          "id": "2128-2",
          "qas": [
            {
              "id": "2128-2-1",
              "question": "新教在教義上強調信徒皆祭司以及什麼樣的理念?",
              "answers": [
                {
                  "id": "1",
                  "text": "因信稱義",
                  "answer_start": 92
                }
              ]
            },
            {
              "id": "2128-2-2",
              "question": "哪本經典為新教的最高權威?",
              "answers": [
                {
                  "id": "1",
                  "text": "聖經",
                  "answer_start": 105
                }
              ]
            },
            {
              "id": "2128-2-3",
              "question": "新教認同幾個唯獨?",
              "answers": [
                {
                  "id": "1",
                  "text": "五個",
                  "answer_start": 171
                }
              ]
            },
            {
              "id": "2128-2-4",
              "question": "文中提及，人唯獨藉信心接受神的赦罪、拯救，此為哪一種唯獨?",
              "answers": [
                {
                  "id": "1",
                  "text": "唯獨信心",
                  "answer_start": 206
                }
              ]
            }
          ]
        },
        {
          "context": "主教制源自天主教的主教制度，幾乎和天主教的主教制度一模一樣，唯一不同的是主教亦可以結婚。天主教的主教制是在使徒們去世後於第二、三世紀興起的主教制度，所以可以說主教制是整個基督宗教中歷史最悠久的神職人員制度。現在行主教制的新教教會已經很少，聖公會就是沿用主教制，從教會制度和禮儀上看來，聖公會基本上屬大公教會傳統。路德宗和衛理公會則由各區會自行選擇使用主教制還是長老制；在香港和澳門，路德會和衛理公會就選用了長老制。然而，在歐洲，例如瑞典、芬蘭、挪威、德國等地，他們則通常採用主教制。長老制，是一個以議會形式管理區會的制度。議會內的成員由各教會選出長老，代表該教會出席會議。顧名思義，長老會就是採用長老制的教會。採用長老制的教會有基督教改革宗長老會、台灣基督長老教會、韓國基督長老教會等。",
          "id": "2128-3",
          "qas": [
            {
              "id": "2128-3-1",
              "question": "新教的主教制度源自於哪一教?",
              "answers": [
                {
                  "id": "1",
                  "text": "天主教",
                  "answer_start": 5
                }
              ]
            },
            {
              "id": "2128-3-2",
              "question": "文中提及，新教的主教可以做什麼?",
              "answers": [
                {
                  "id": "1",
                  "text": "結婚",
                  "answer_start": 41
                }
              ]
            },
            {
              "id": "2128-3-3",
              "question": "哪個會屬於大公教會傳統?",
              "answers": [
                {
                  "id": "1",
                  "text": "聖公會",
                  "answer_start": 142
                }
              ]
            },
            {
              "id": "2128-3-4",
              "question": "以議會形式管理區會的制度，名為?",
              "answers": [
                {
                  "id": "1",
                  "text": "長老制",
                  "answer_start": 241
                }
              ]
            }
          ]
        }
      ]
    }
  ]
}
  
  ```

## Copyright Notice 版权声明

本资料集整理、改编自维基百科，其内容以CC-BY-SA 3.0条款发布。
台达电子对于本资料集内容之正确性不为任何担保，且不就因使用或倚赖本资料集而引致的任何损失，承担任何责任。
CC-BY-SA 3.0相关条款请参考以下连结
http://creativecommons.org/licenses/by-sa/3.0/

DRCD is compiled and adapted from Wikipedia and its content is published under the terms of CC-BY-SA 3.0. Delta Electronics, Inc. makes no representations or warranties of the correctness of the contents of DRCD and will not be liable for any loss or damage arising from the use or reliance on DRCD. 

CC-BY-SA 3.0 can be found at

http://creativecommons.org/licenses/by-sa/3.0/


## Contact us 联系作者

- 资料所有： <a href="http://www.deltaww.com/about/drc_ch.aspx?secID=5&pid=4&tid=1&hl=zh-TW">台达研究院Delta Research Center</a>
- Email: <a href="mailto:cchieh.shao@deltaww.com">cchieh.shao@deltaww.com</a>

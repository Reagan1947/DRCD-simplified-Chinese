# DRCD Simplified Chinese 
> This is simplified Chinese version of DRCD SQuAD1.0 Dataset. 
> 这是简体中文版的DRCD的SQuAD1.0数据集
>
> WARNING: 尚未使用run_squad.py程序对简体中文版本的可用性进行验证。请小心使用！

> 以下是繁体DRCD数据集原始版说明

台达阅读理解资料集 Delta Reading Comprehension Dataset (DRCD) 属于通用领域繁体中文机器阅读理解资料集。
本资料集期望成为适用于迁移学习之标准中文阅读理解资料集。
本资料集从2,108篇维基条目中整理出10,014篇段落，并从段落中标注出30,000多个问题

关于资料集之更详细资讯请洽询论文：
For more information please refer to Paper https://arxiv.org/abs/1806.00920

## DRCD数据问题

DRCD数据在应用到Google/Research/Bert/SQuAD ^[1] 中的`run_squad.py`程序时，似乎给出了`list index out of range`。

目前认为错误的原因是数据的`answer_start`在个别数据中出现了错误。

通过修改`run_squad.py`文件相应部分，使用`try`与`except`进行debug。

以下为debug修改后程序举例：

```python
try:
    start_position = char_to_word_offset[answer_offset]
except:
    print(answer)
try:
    end_position = char_to_word_offset[answer_offset + answer_length - 1]
except:
    print(answer)
```

[1]Google/Research/Bert/SQuAD Link: https://github.com/google-research/bert

**/TIP: 将可能在近期给出订正版本**

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
          "context": "基督新教与天主教均继承普世教会历史上许多传统教义，如三位一体、圣经作为上帝的启示、原罪、认罪、最后审判等等，但有别于天主教和东正教，新教在行政上没有单一组织架构或领导，而且在教义上强调因信称义、信徒皆祭司， 以圣经作为最高权威，亦因此否定以教宗为首的圣统制、拒绝天主教教条中关于圣传与圣经具同等地位的教导。新教各宗派间教义不尽相同，但一致认同五个唯独：唯独恩典：人的灵魂得拯救唯独是神的恩典，是上帝送给人的礼物。唯独信心：人唯独藉信心接受神的赦罪、拯救。唯独基督：作为人类的代罪羔羊，耶稣基督是人与上帝之间唯一的调解者。唯独圣经：唯有圣经是信仰的终极权威。唯独上帝的荣耀：唯独上帝配得讚美、荣耀",
          "id": "2128-2",
          "qas": [
            {
              "id": "2128-2-1",
              "question": "新教在教义上强调信徒皆祭司以及什麽样的理念?",
              "answers": [
                {
                  "id": "1",
                  "text": "因信称义",
                  "answer_start": 92
                }
              ]
            },
            {
              "id": "2128-2-2",
              "question": "哪本经典为新教的最高权威?",
              "answers": [
                {
                  "id": "1",
                  "text": "圣经",
                  "answer_start": 105
                }
              ]
            },
            {
              "id": "2128-2-3",
              "question": "新教认同几个唯独?",
              "answers": [
                {
                  "id": "1",
                  "text": "五个",
                  "answer_start": 171
                }
              ]
            },
            {
              "id": "2128-2-4",
              "question": "文中提及，人唯独藉信心接受神的赦罪、拯救，此为哪一种唯独?",
              "answers": [
                {
                  "id": "1",
                  "text": "唯独信心",
                  "answer_start": 206
                }
              ]
            }
          ]
        },
        {
          "context": "主教制源自天主教的主教制度，几乎和天主教的主教制度一模一样，唯一不同的是主教亦可以结婚。天主教的主教制是在使徒们去世后于第二、三世纪兴起的主教制度，所以可以说主教制是整个基督宗教中历史最悠久的神职人员制度。现在行主教制的新教教会已经很少，圣公会就是沿用主教制，从教会制度和礼仪上看来，圣公会基本上属大公教会传统。路德宗和卫理公会则由各区会自行选择使用主教制还是长老制；在香港和澳门，路德会和卫理公会就选用了长老制。然而，在欧洲，例如瑞典、芬兰、挪威、德国等地，他们则通常採用主教制。长老制，是一个以议会形式管理区会的制度。议会内的成员由各教会选出长老，代表该教会出席会议。顾名思义，长老会就是採用长老制的教会。採用长老制的教会有基督教改革宗长老会、台湾基督长老教会、韩国基督长老教会等。",
          "id": "2128-3",
          "qas": [
            {
              "id": "2128-3-1",
              "question": "新教的主教制度源自于哪一教?",
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
              "question": "文中提及，新教的主教可以做什麽?",
              "answers": [
                {
                  "id": "1",
                  "text": "结婚",
                  "answer_start": 41
                }
              ]
            },
            {
              "id": "2128-3-3",
              "question": "哪个会属于大公教会传统?",
              "answers": [
                {
                  "id": "1",
                  "text": "圣公会",
                  "answer_start": 142
                }
              ]
            },
            {
              "id": "2128-3-4",
              "question": "以议会形式管理区会的制度，名为?",
              "answers": [
                {
                  "id": "1",
                  "text": "长老制",
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

- 资料所有: <a href="http://www.deltaww.com/about/drc_ch.aspx?secID=5&pid=4&tid=1&hl=zh-TW">台达研究院Delta Research Center</a>
- Email: <a href="mailto:cchieh.shao@deltaww.com">cchieh.shao@deltaww.com</a>

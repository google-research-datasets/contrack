# The Context Tracking Dataset

**Contact -** contrack-dev@google.com

## Overview

The **Context Tracking** dataset consists of annotated human-human social
conversations. Each conversation contains annotations for the people and
location entities mentioned, their properties and the relationships between
them. The annotated data enables several subtasks like slot tagging, coreference
resolution, resolving plural mentions and entity linking. In addition, the
turn-by-turn annotations also enable the development of computationally
efficient models which can handle long conversations. The conversations cover a
wide range of topics mentioning multiple people and locations. The dataset
contains unseen entity names and topics in the test set to quantify the
generalization capability of various modeling approaches.

**The datasets are provided "AS IS" without any warranty, express or implied.
Google disclaims all liability for any damages, direct or indirect, resulting
from the use of this dataset.**

## Important Links

*   [Paper - A Unified Approach to Entity-Centric Context Tracking in Social
    Conversations](https://arxiv.org/abs/2201.12409)
*   [Data processing and modeling code](https://github.com/google-research/google-research/tree/master/contrack)

## Data

The Context Tracking dataset consists of human-human conversations with
annotations for people and location entities along with additional data for each
entity. These conversations are meant to represent typical interactions on
instant messaging platforms like Google Messages, iMessage, WhatsApp etc,
between two people. For each turn or message, the person sending the message is
referred to as the "sender". The conversations and annotations were created by
hundreds of paid crowd-workers, followed by a round of verification and
filtering. Each conversation is seeded by a **scenario** describing the overall
flow of the conversation. Scenarios are not repeated across the `train` and
`test` sets. The data is in the format of text files and can be processed using
the data processing code
[here](https://github.com/google-research/google-research/tree/master/contrack)
which also contains the implementation of a baseline end-to-end model for this
task. Additional information about the dataset, the data collection process and
quality control details can be found in the
[paper](https://arxiv.org/abs/2201.12409).

### Conversation Representation

Each conversation contains metadata comprising of the conversation ID, the names
of the participants and the initial annotation. The metadata is followed by a
sequence of turns. To mimic natural conversations, the sequence of turns is not
always strictly alternating between the two participants. Each turn consists of
3 parts separated by the `|` character. The first part represents the
sender/speaker of the turn. The second part represents the text content of the
turn. For data processing convenience, all non alpha-numeric and non-space
characters have been removed. The third part contains the annotations descriced
in the `Annotation Format` section. Conversations are separated by a blank line.

### Annotation Format

As mentioned in the Converstation Representation section, the third part of each
turn contains the annotation section. The annotations contain information
related to the people and location entities mentioned in the conversation. The
annotation data for each entity reference is enclosed by square brackets `[]`.
Each annotation consists of 3 parts:

1.  The name or unique identifier of the entity in the conversation.
2.  The properties of the entity that can be inferred from the conversation.
3.  The span of tokens representing each entity reference.

For entities representing people, the properties annotated include the
grammatical gender, plurality (typically this refers to a group of people) and
in case of plural entities, the constituent singular entities, if they have been
mentioned so far in the conversation. For location entities, the properties
indicate the plurality of the entity and the constituent singular entities for a
plural entity. The span is represented as `start_token_index-end_token_index`
where the token indexes represent 0-based indices into the tokens of the
conversation turn. Both entries of the span are inclusive,

## License

The Context Tracking dataset are released under
[**CC BY-SA 4.0**](https://creativecommons.org/licenses/by-sa/4.0/) license. For
the full license, see [LICENSE](LICENSE). Please cite the following paper if you
use the dataset in your work:

```shell
@article{DBLP:journals/corr/abs-2201-12409,
  author    = {Ulrich R{\"{u}}ckert and
               Srinivas Sunkara and
               Abhinav Rastogi and
               Sushant Prakash and
               Pranav Khaitan},
  title     = {A Unified Approach to Entity-Centric Context Tracking in Social Conversations},
  journal   = {CoRR},
  volume    = {abs/2201.12409},
  year      = {2022},
  url       = {https://arxiv.org/abs/2201.12409},
  eprinttype = {arXiv},
  eprint    = {2201.12409},
  timestamp = {Wed, 02 Feb 2022 15:00:01 +0100},
  biburl    = {https://dblp.org/rec/journals/corr/abs-2201-12409.bib},
  bibsource = {dblp computer science bibliography, https://dblp.org}
}
```

## Dataset Metadata

The following table is necessary for this dataset to be indexed by search
engines such as <a href="https://g.co/datasetsearch">Google Dataset Search</a>.
<div itemscope itemtype="http://schema.org/Dataset">
<table>
  <tr>
    <th>property</th>
    <th>value</th>
  </tr>
  <tr>
    <td>name</td>
    <td><code itemprop="name">Context Tracking dataset</code></td>
  </tr>
  <tr>
    <td>alternateName</td>
    <td><code itemprop="alternateName">Contrack dataset</code></td>
  </tr>
  <tr>
    <td>url</td>
    <td><code itemprop="url">https://github.com/google-research-datasets/context-tracking</code></td>
  </tr>
  <tr>
    <td>description</td>
    <td><code itemprop="description">The dataset consists of annotated human-human conversations in various social settings. Along with the conversations, the dataset contains annotations for people and location entities present in the conversation along with the properties of those entities and their relationships. The annotated data enables several subtasks like slot tagging, coreference resolution, resolving plural mentions and entity linking.</code></td>
  </tr>
  <tr>
    <td>provider</td>
    <td>
      <div itemscope itemtype="http://schema.org/Organization" itemprop="provider">
        <table>
          <tr>
            <th>property</th>
            <th>value</th>
          </tr>
          <tr>
            <td>name</td>
            <td><code itemprop="name">Google</code></td>
          </tr>
          <tr>
            <td>sameAs</td>
            <td><code itemprop="sameAs">https://en.wikipedia.org/wiki/Google</code></td>
          </tr>
        </table>
      </div>
    </td>
  </tr>
  <tr>
    <td>citation</td>
    <td><code itemprop="citation">https://identifiers.org/arxiv:2201.12409</code></td>
  </tr>
</table>
</div>

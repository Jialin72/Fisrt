# Fisrt project
## 主要内容介绍
这是为了M大学的network in python（https://github.com/sambhipiyush/Applied-Social-Network-Analysis-in-Python-University-of-Michigan） 的学习而开始的项目。
这个项目主要是几个方面的内容：1 是network的现象以及其研究价值；2 是python是如何定义network的（python如何表示network）； 3 network的相关measurement
（为了防止忘记MD文件规则，（我自己）可以浏览 [MD认识与入门]（https://sspai.com/post/25137））

## 1 network 现象以及其研究价值
- 尽管network概念并不是一个新的事物，但是近年来network终于在大数据环境下获得新的生命力。如果用network观点来观察我们的工作（或者其他）对象，
  我们发现很多现象都可以看作是network。比如，
    *social network* 
    在一个班级里，老师和同学之间的交流构成一个网络。
    *transportionion network*
    公交车在各个站点之间运行构成一个网络。
    *webpage network*
    比如网络上blogs,一个blog 与其他blog相联系。这些blogs（如果是入M老师所讲的political blogs, 就会发现左翼的政治人员往往和左翼的人员相联系，右翼分子与右翼分子相联系）
    就形成信息网络。
 - 可以看出很多现象都可以用network来描述，这就是研究network最主要的动机。可以想象，如果能够把我们所感兴趣的想象描述成network，那么我们就可以借助network的知识来增进我们对该现象的理解
## 2 python是如何定义network
  python 开发团队开发了networkX库，可供network 研究。在具体学习networkX之前，需要解决的问题是，*python 如何定义network*。
- 从前面的现象来看，network主要特征是由能够形成联系（link, connection, dependency）的对象，以及多个这种对象形成的link, connection or dependency 构成。比如班级里面形成联系的对象是老师   和学生（当然还有其他事物对象也能形成network，但是这里假定我们只关心老师和学生群体），他们互动形成了联系，比如老师对每个学生的作业修改工作形成了老师和学生的联系，比如老师和同学们之间的朋   友关系形成的网络。再比如blogs例子中，blog的主人是形成关系的对象，所形成的关系是connections between blogs through URLs. 
- 那么如何形成一般性的network定义？ 
  * 在图论中，将这些关系定义为nodes 和 edges。nodes 就是形成联系的对象，edges表示connection,link or dependency.
  > A Network , which we also call a Graph, is a representation of connections among different sets. 
  > This is a network between people and the edges here represent friendship, marital ties and family ties among 2,200 people
  > Nodes : People
  > Edges : Friendship, marital, or family ties
  那么关键在python 如何基于nodes 和edges 来处理network, networkx。
  'import networkx as nx  
  G = nx.Graph()
  G.add_edges('A', 'B')
  G.add_edges('B', 'C') '
### network 分类
  -undirected network 
  如果edges 没有方向性，或者说edges方向没有什么意义。
  >These are undirected networks, meaning the edges don't have any direction, or that the direction of the edge is not really important
  -directed network
  edges 方向具有重要意义。(我目前主要关注这一类，因为这一类与我感兴趣的现象相关)
  >These are directed networks, meaning the edges have direction, or that the direction of the edge is really important
  >In NetworkX we use the class DiGraph (Directed Graph) to represent these types of networks
  - weighted network
  edges 被赋予了一定的权重。
  >Weighted Network is a network where edges are assigned a particular weight, typically a numerical weight, that has some meaning in the relationship between the two nodes
  >The intuition here is that in some networks
  > *Not all relationships are equal*
  > *Some edges carry different weight than others, so we want a way of capturing this*
  > A network where the nodes are people and then the edges represent how many times they had lunch together. These are coworkers
  > In NetworkX, we can represent these types of networks also by using the class Graph
  > But what have to do is when we add an edge, for example the edge A, B, we have to add an attribute weight as well
  >  import networkx as nx
 ' G = nx.Graph()
  G.add_edges('A', 'B', weight=6)
  G.add_edges('B', 'C', weight=13)'
  *可以看出network中edges是储存重要信息的对象，通过edges的性质来对network进行分类的。networkX中可以按照不同的类型的network构建不同的类，这些类主要是class Graph 和DiGraph 两个我感兴趣的类。在不同的类中，主要通过类的方法为edges 添加属性 attributes来描述network的。 比如，加weight，加relation 等属性*
  > Edges can carry many other labels or Attributes
>Relation
>Friend
>Family
>Coworker
>Neighbor

'import networkx as nx
 G = nx.Graph()
 G.add_edges('A', 'B', relation='friend')
 G.add_edges('B', 'C', relation='coworker')
 G.add_edges('D', 'E', relation='family') '

*更具介绍，还有一类network是MultiGraph network.
特征是：
>A pair of nodes can have different types of relationships simultaneously
>Intuition for multigraphs is that for a single pair of of nodes, there is no reason why they shouldn't be able to have many different relationships at the same time
>MultiGraphs Network is a network where multiple edges can connect the same pair of nodes. They're also called parallel edges
这种MutilGraph 在networkX中有 MultiGraph类来描述
 ' import networkx as nx
  G = nx.MultiGraph()
  G.add_edges('A', 'B', relation='friend')
  G.add_edges('A', 'B', relation='neighbor')
  G.add_edges('G', 'F', relation='family')
  G.add_edges('G', 'F', relation='coworker') ' *
  

 
  

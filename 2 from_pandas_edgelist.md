# from_pandas_edgelist (来自help文件)& 	[pd.read_csv](https://www.cnblogs.com/traditional/p/12514914.html) 
Definition : from_pandas_edgelist(df, source="source", target="target", edge_attr=None, create_using=None, edge_key=None)
Returns a graph from Pandas DataFrame containing an edge list.

The Pandas DataFrame should contain at least two columns of node names and zero or more columns of edge attributes.**Each row will be processed as one edge instance.

Note: This function iterates over DataFrame.values, which is not guaranteed to retain the data type across columns in the row. This is only a problem if your row is entirely numeric and a mix of ints and floats. In that case, all values will be returned as floats. See the DataFrame.iterrows documentation for an example.

## Parameters

**df**: Pandas DataFrame
An edge list representation of a graph

**source**: str or int
**A valid column name (string or integer) for the source nodes (for the directed case).

**target**: str or int
**A valid column name (string or integer) for the target nodes (for the directed case).

**edge_attr**: str or int, iterable, True, or None
**A valid column name (str or int) or iterable of column names that are used to retrieve items and add them to the graph as edge attributes. If True, all of the remaining columns will be added. If None, no edge attributes are added to the graph.

**create_using**: NetworkX graph constructor, optional (default=nx.Graph)
Graph type to create. If graph instance, then cleared before populated.

**edge_key**:str or None, optional (default=None)
**A valid column name for the edge keys (for a MultiGraph). The values in this column are used for the edge keys when adding edges if create_using is a multigraph.

See Also

to_pandas_edgelist


The k-d tree-building algorithms are described in the following online articles.

http://www.jcgt.org/published/0004/01/03/

https://arxiv.org/abs/1410.5420

The Journal of Computer Graphics Techniques article contains a detailed description of an O(kn logn) k-d tree building algorithm and compares the performance of that algorithm to the performance of an O(n logn) algorithm.

The arXiv article includes an appendix that describes improvements to two k-d tree-building algorithms that were implemented following the description of those algorithms in the Journal of Computer Graphics Techniques article. A copy of the arXiv article is available in this master branch.

The source files “kdTreeKnlogn.cpp” and “kdTreeNlogn.cpp” are implementations that build a balanced k-d tree.

The source files "kdTreeMapKnlogn.cpp", "kdTreeMapNlogn.cpp", "kdTreeKmapKnlog.cpp", and "kdTreeKmapNlogn.cpp" are implementations that build a balanced k-d tree-based key-to-value map. The latter two implementations of the key-to-value map execute twice as rapidly as the former two implementations. See the arXiv article for details.

All six source files include algorithms that search a k-d tree (1) for all points that lie inside a k-dimensional hyper-rectangular region; (2) for the m nearest neighbors to a query point sorted according to their distances to the query point via a priority queue; and (3) for the reverse nearest neighbors to each point in the k-d tree, where the reverse nearest neighbors to a given point are defined as the set of points to which that point is a nearest neighbor. All six implementations build a k-d tree and search a k-dimensional hyper-rectangular region using multiple threads. The nearest-neighbors-search and reverse-nearest-neighbors-search algorithms are each single threaded.

The command-line options for controlling execution of the k-d tree-building programs are as follows.

-n The number of randomly generated points used to build the k-d tree

-m The number of nearest neighbors kept on the priority queue created when searching the k-d tree for nearest neighbors

-x The number of duplicate points added to test removal of duplicate points

-d The number of dimensions (k) of the k-d tree; not applicable to the kdTreeKmapKnlogn.cpp and kdTreeKmapNlogn.cpp programs because for these programs the number of dimensions is specified at compile time

-t The number of threads used to build and region-search the k-d tree

-s The search distance used for region search

-p The maximum number of nodes to print when reporting k-d tree search results

-b Enable nearest neighbors by exhaustive search for comparison to k-d tree search

-c Enable region search by exhaustive search for comparison to k-d tree search

-r Enable construction of nearest-neighbors and reverse-nearest-neighbors maps

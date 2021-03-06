
 

 

 

 

 

([C++](Cpp.md)) [std::set\_union](CppSet_union.md)
====================================================

 

[std::set\_union](CppSet_union.md) is an [STL](CppStl.md)
[algorithm](CppAlgorithm.md) to create the union set of two sorted
[containers](CppContainer.md), neither of which must hold duplicate
entries.

 

  -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` #include <algorithm> #include <cassert> #include <vector>  int main() {   //Create the first sorted vector   std::vector<int> v;   v.push_back(1); //Unique to v   v.push_back(2); //Present in v and w   //Create the second sorted vector   std::vector<int> w;   w.push_back(2); //Present in v and w   w.push_back(3); //Unique to w   //Create the set union in x   std::vector<int> x;    std::set_union(     v.begin(),v.end(),     w.begin(),w.end(),     std::back_inserter(x));    //Check if algorithm worked as expected   assert(x.size() == 3);   assert(x[0] == 1); //Unique in v   assert(x[1] == 2); //Present in both v and w   assert(x[2] == 3); //Unique in w }`
  -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

External links
--------------

 

-   [Cplusplus.com page about
    std::set\_union](http://www.cplusplus.com/reference/algorithm/set_union)

 

 

 

 

 

 


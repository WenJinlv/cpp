
 

 

 

 

 

([C++](Cpp.md)) [std::search](CppStdSearch.md)
=============================================

 

[std::search](CppStdSearch.md) is an [STL](CppStl.md)
[algorithm](CppAlgorithm.md) for searching a sequence of elements in
[containers](CppContainer.md). It is similar to
[std::find](CppStdFind.md), except that [std::find](CppStdFind.md) searches
for a single element.

 

 

 

 

 

Example
-------

 

Assume you work with a [std::vector](CppStdVector.md) of
[integers](CppInt.md) in which two sequences are forbidden: zero-zero
and one-zero. With [std::search](CppStdSearch.md) these sequences can be
used to find if our exemplary [std::vector](CppStdVector.md) is valid.

 

  -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` #include <algorithm> #include <cassert> #include <vector>  int main() {   std::vector<int> v;   v.push_back(0);   v.push_back(1);   v.push_back(0);   v.push_back(0);   v.push_back(2);   v.push_back(0);    //Two consequtive zeroes are forbidden   std::vector<int> f1;   f1.push_back(0);   f1.push_back(0);    //A one followed by a two is forbidden   std::vector<int> f2;   f2.push_back(1);   f2.push_back(2);    assert(std::search(v.begin(),v.end(),f1.begin(),f1.end())     != v.end()     && "Assume forbidden sequence 1 is detected");    assert(std::search(v.begin(),v.end(),f2.begin(),f2.end())     == v.end()     && "Assume forbidden sequence 2 is not present"); }`
  -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

Example: [SeperateString](CppSeperateString.md)
------------------------------------------------

 

  -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` #include <vector> #include <string> #include <cassert> #include <algorithm>   //From http://www.richelbilderbeek.nl/CppSeperateString.htm const std::vector<std::string> SeperateString (   const std::string& input,   const std::string& seperator) {   std::vector<std::string> v;   typedef std::string::const_iterator Iterator;   const Iterator end = input.end();   Iterator i1 = input.begin();   {     //Copy until first comma     Iterator i2 = std::search(i1,end,seperator.begin(), seperator.end());     assert(i1!=i2);     std::string s;     std::copy(i1,i2, std::back_inserter(s));     v.push_back(s);     i1 = i2;   }   while (i1!=end)   {     //Copy from comma to (comma || end)     Iterator i2 = std::search(i1 + 1,end,seperator.begin(), seperator.end());     assert(i1!=i2);     assert(i2 == end || std::equal(seperator.begin(),seperator.end(),i2));     std::string s;     std::copy(i1+1,i2, std::back_inserter(s));     v.push_back(s);     i1 = i2;   }   return v; }`
  -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

 


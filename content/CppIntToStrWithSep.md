
 

 

 

 

 

([C++](Cpp.md)) [IntToStrWithSep](CppIntToStrWithSep.md)
==========================================================

 

[IntToStrWithSep](CppIntToStrWithSep.md) is an
[int](CppInt.md)/[cln::cl\_I](CppCl_I.md) [conversion](CppConvert.md)
[code snippet](CppCodeSnippets.md) to [convert](CppConvert.md) an
[int](CppInt.md) to [std::string](CppStdString.md) and adding the
thousands seperators.

 

[IntToStrWithSep](CppIntToStrWithSep.md) has multiple flavors:

1.  [STL](CppStl.md) [IntToStrWithSep](CppIntToStrWithSep.md)
2.  [CLN](CppCln.md) [IntToStrWithSep](CppIntToStrWithSep.md)

 

 

 

 

 

[STL](CppStl.md) [IntToStrWithSep](CppIntToStrWithSep.md)
-----------------------------------------------------------

 

  -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` #include <iostream> #include <string> #include <boost/lexical_cast.hpp>  ///IntToStrWithSep converts an integer to std::string ///and adds thousands seperators. ///From http://www.richelbilderbeek.nl/CppIntToStrWithSep.htm const std::string IntToStrWithSep(int i) {   std::string s = boost::lexical_cast<std::string>(i%10);   i/=10;   int d = 1;   while (i)   {     s = boost::lexical_cast<std::string>(i%10)       + (d % 3 == 0 ? "," : "")       + s;     i/=10;     ++d;   }   return s; }  int main() {   int i=1;   for (int n_zeros=0; n_zeros!=10; ++n_zeros)   {     std::cout       << IntToStrWithSep(i)       << ' '       << IntToStrWithSep(-i)       << '\n';     i*=10;   } }`
  -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

Screen output:

 

  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` 1 -1 10 -10 100 -100 1,000 -1,000 10,000 -10,000 100,000 -100,000 1,000,000 -1,000,000 10,000,000 -10,000,000 100,000,000 -100,000,000 1,000,000,000 -1,000,000,000`
  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

[CLN](CppCln.md) [IntToStrWithSep](CppIntToStrWithSep.md)
-----------------------------------------------------------

 

  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` //--------------------------------------------------------------------------- #include <iostream> #include <string> //--------------------------------------------------------------------------- #include <boost/lexical_cast.hpp> //--------------------------------------------------------------------------- #include <cln/cln.h> //--------------------------------------------------------------------------- ///IntToStrWithSep converts an integer to std::string ///and adds thousands seperators. ///From http://www.richelbilderbeek.nl/CppIntToStrWithSep.htm const std::string IntToStrWithSep(cln::cl_I i) {   std::string s     = boost::lexical_cast<std::string>(cln::mod(i,10));   i = cln::floor1(i,10);   int d = 1;   while (!cln::zerop(i))   {     s = boost::lexical_cast<std::string>(cln::mod(i,10))       + (d % 3 == 0 ? "," : "")       + s;     i = cln::floor1(i,10);     ++d;   }   return s; } //--------------------------------------------------------------------------- int main() {   const cln::cl_I i("123456789012345678901234567890");   std::cout << "i without seperators: " << i << '\n';   const std::string s = IntToStrWithSep(i);   std::cout << "i with seperators: " << s << '\n'; } //---------------------------------------------------------------------------`
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

Screen output:

 

  --------------------------------------------------------------------------------------------------------------------
  ` i without seperators: 123456789012345678901234567890 i with seperators: 123,456,789,012,345,678,901,234,567,890`
  --------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

 


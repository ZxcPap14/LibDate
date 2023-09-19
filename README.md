# LibDate
Create by: Денис Казанцев & Артем Николаев

-lib

    using System;
    using System.Collections.Generic;
    using System.Diagnostics;
    using System.Linq;
    using System.Text;
    using System.Threading.Tasks;
    namespace StringLib
    {
        public class StringClass
        {
    
            /// <summary>
            /// Метод принимает в качестве параметра строку textString.
            /// Предполагается, что строка может быть пустой или содержать произвольный набор символов.
            /// </summary>
            /// <param name="textString"></param>
            /// <param name="typeDate"></param>
            /// <returns>
            /// Метод возвращает true, если входная строка является датой в корректном формате, в противном случае возвращает - false.
            /// </returns>
            public static bool StringParse(string textString, int typeDate)
            {
                int[] arrDate = new int[13];
                DateTime dateResult;
                DateTime maxdt = new DateTime(9998);
               
                    if (!DateTime.TryParse(textString, out dateResult))
                    {
                        return false;
                    }
                    return true;
            }
        }
    }

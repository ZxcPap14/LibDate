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

-Tests

    
                using Microsoft.VisualStudio.TestTools.UnitTesting;
            using System;
            using StringLib;
            
            namespace StringLibTests0
            {
                /// <summary>
                /// Формат - Дата
                /// </summary>
                [TestClass]
                public class UnitTest1
                {
                    [TestMethod]
                    public void StringLib_CorrectDate_ReturnedTrue()
                    {
                        string TextDate = "30.05.2006";
                        int typeDate = 10;
                        //Act
                        bool result = StringClass.StringParse(TextDate, typeDate);
                        //Assert
                        Assert.IsTrue(result);
                    }
                    [TestMethod]
                    public void StringLib_Empty_ReturnedFalse()
                    {
                        string TextDate = " ";
                        int typeDate = 0;
                        //Act
                        bool result = StringClass.StringParse(TextDate, typeDate);
                        //Assert
                        Assert.IsFalse(result);
                    }
                    [TestMethod]
                    public void MStringLib_MagicDate_ReturnedTrue()
                    {
                        string TextDate = "01.01.1900";
                        int typeDate = 10;
                        //Act
                        bool result = StringClass.StringParse(TextDate, typeDate);
                        //Assert
                        Assert.IsTrue(result);
                    }
                    [TestMethod]
                    public void StringLib_UnixZero_ReturnedTrue()
                    {
                        string TextDate = "01.01.1970";
                        int typeDate = 10;
                        //Act
                        bool result = StringClass.StringParse(TextDate, typeDate);
                        //Assert
                        Assert.IsTrue(result);
                    }
            
                    [TestMethod]
                    public void StringLib_IncorrectDate1_ReturnedFalse()
                    {
                        string TextDate = "00.12.2023";
                        int typeDate = 10;
                        //Act
                        bool result = StringClass.StringParse(TextDate, typeDate);
                        //Assert
                        Assert.IsFalse (result);
                    }
                    [TestMethod]
                    public void StringLib_IncorrectDate2_ReturnedFalse()
                    {
                        string TextDate = "30.02.23";
                        int typeDate = 10;
                        //Act
                        bool result = StringClass.StringParse(TextDate, typeDate);
                        //Assert
                        Assert.IsFalse(result);
                    }
                    [TestMethod]
                    public void StringLib_IncorrectMonth_ReturnedFalse()
                    {
                        string TextDate = "12.15.2023";
                        int typeDate = 10;
                        //Act
                        bool result = StringClass.StringParse(TextDate, typeDate);
                        //Assert
                        Assert.IsFalse(result);
                    }
                    [TestMethod]
                    public void StringLib_IncorrectYear_ReturnedFalse()
                    {
                        string TextDate = "12.15.0000";
                        int typeDate = 10;
                        //Act
                        bool result = StringClass.StringParse(TextDate, typeDate);
                        //Assert
                        Assert.IsFalse(result);
                    }
                    [TestMethod]
                    public void StringLib_IncorrectLeapYear_ReturnedFalse()
                    {
                        string TextDate = "29.02.2023";
                        int typeDate = 10;
                        //Act
                        bool result = StringClass.StringParse(TextDate, typeDate);
                        //Assert
                        Assert.IsFalse(result);
                    }
                    [TestMethod]
                    public void StringLib_ZeroInDate1_ReturnedFalse()
                    {
                        string TextDate = "00.00.0000";
                        int typeDate = 10;
                        //Act
                        bool result = StringClass.StringParse(TextDate, typeDate);
                        //Assert
                        Assert.IsFalse(result);
                    }
                    [TestMethod]
                    public void StringLib_ZeroInDate2_ReturnedFalse()
                    {
                        string TextDate = "12.03.0000";
                        int typeDate = 10;
                        //Act
                        bool result = StringClass.StringParse(TextDate, typeDate);
                        //Assert
                        Assert.IsFalse(result);
                    }
                    [TestMethod]
                    public void StringLib_ZeroInDate3_ReturnedFalse()
                    {
                        string TextDate = "12.00.1989";
                        int typeDate = 10;
                        //Act
                        bool result = StringClass.StringParse(TextDate, typeDate);
                        //Assert
                        Assert.IsFalse(result);
                    }
                    [TestMethod]
                    public void StringLib_ZeroInDate4_ReturnedFalse()
                    {
                        string TextDate = "00.03.1989";
                        int typeDate = 10;
                        //Act
                        bool result = StringClass.StringParse(TextDate, typeDate);
                        //Assert
                        Assert.IsFalse(result);
                    }
                    [TestMethod]
                    public void StringLib_MaxNumber1_ReturnedFalse()
                    {
                        string TextDate = "99.99.9999";
                        int typeDate = 10;
                        //Act
                        bool result = StringClass.StringParse(TextDate, typeDate);
                        //Assert
                        Assert.IsFalse(result);
                    }
                    [TestMethod]
                    public void StringLib_MaxnumberinYear_ReturnedTrue()
                    {
                        string TextDate = "12.03.9999";
                        int typeDate = 10;
                        //Act
                        bool result = StringClass.StringParse(TextDate, typeDate);
                        //Assert
                        Assert.IsTrue(result);
                    }
                    [TestMethod]
                    public void StringLib_MaxNumbersInMonth_ReturnedFalse()
                    {
                        string TextDate = "12.99.1989";
                        int typeDate = 10;
                        //Act
                        bool result = StringClass.StringParse(TextDate, typeDate);
                        //Assert
                        Assert.IsFalse(result);
                    }
                    [TestMethod]
                    public void StringLib_MaxNumbersInDays_ReturnedFalse()
                    {
                        string TextDate = "99.03.1989";
                        int typeDate = 10;
                        //Act
                        bool result = StringClass.StringParse(TextDate, typeDate);
                        //Assert
                        Assert.IsFalse(result);
                    }
            
            
                }
            }


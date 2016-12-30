using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using HtmlAgilityPack;
using System.IO;

namespace HTML_parser
{

    class Program
    {
        static void Main(string[] args)
        {
            string current_time=DateTime.Now.ToString();

            HtmlWeb web = new HtmlWeb();
          
            HtmlDocument html = web.Load("https://ticketcamp.net/aqours-tickets/?ref=search-history");

            HtmlNode[] price = html.DocumentNode.SelectNodes("//span[@class=\"ticket-price\"]").ToArray();

            HtmlNode node = html.DocumentNode.SelectSingleNode("//li[@class=\"column price clickable\"]/a");

            string dest = node.GetAttributeValue("href", "");

            //Console.WriteLine(dest); //url 표시.

            string url_value = dest;

            HtmlDocument subhtml = web.Load(url_value);

            HtmlNode[] order = subhtml.DocumentNode.SelectNodes("//strong").ToArray();  //모든 string에서 비교하는 구문 필요.

            string contain_order = order[0].InnerHtml;

            HtmlNode[] day = subhtml.DocumentNode.SelectNodes("//head").ToArray();

            string contain_day = day[0].InnerHtml;

            //Console.WriteLine(day[0].InnerHtml);
            

            bool isThereOrder_one = contain_order.Contains("1次");
            bool isThereOrder_two = contain_order.Contains("2次");
            bool isThereOrder_first = contain_order.Contains("最速");
            bool isThereDay_25_0 = contain_day.Contains("2/25");
            bool isThereDay_25_1 = contain_day.Contains("25");
            bool isThereDay_26_0 = contain_day.Contains("2/26");
            bool isThereDay_26_1 = contain_day.Contains("26");

            Console.WriteLine("최저가 티켓 정보입니다.");

                if (isThereOrder_one == true|| isThereOrder_first == true)
                {
                    Console.Write("1차 선행티켓 ");

                }
                else if (isThereOrder_two == true)
                {
                    Console.Write("2차 선행티켓 ");
                }

                else
                {
                    Console.Write("1차 2차 불명 ");
                }

          if (isThereDay_25_0 == true|| isThereDay_25_1 == true)
            {
                Console.Write("2/25 ");
            }
          else if(isThereDay_26_0 == true || isThereDay_26_1 == true)
            {
                Console.Write("2/26 ");
            }
            else
            {
                Console.Write("날짜 불명의 ");
            }

            string en = "엔";
           // Console.Write("최저가 ");
            Console.WriteLine(price[0].InnerHtml+en);

            Console.WriteLine(current_time);

            string path = @"c:\Temp\log.txt";
            string textValue = System.IO.File.ReadAllText(path);
            bool isThereURL = textValue.Contains(dest);
            if(isThereURL==true)
            {
                Console.WriteLine("이전 최저가 티켓은 팔리지 않았습니다.");
                
            }
            else
            {
                Console.WriteLine("이전 최저가 티켓은 팔렸습니다.");
            }
            string _Filestr=(@"C:\Temp\log.txt");
            System.IO.FileInfo fi = new System.IO.FileInfo(_Filestr);
            if(fi.Exists)
            {
                //파일 존재
            }
            else
            {
                //파일 없음
                using (StreamWriter wr = new StreamWriter(@"C:\Temp\data.txt"))

            }

            Console.ReadKey();

        }
    }
}

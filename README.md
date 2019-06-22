using System;
using System.Collections.Generic;
using System.Linq;

namespace LastStop
{
    class Program
    {
        static void Main(string[] args)
        {
            List<int> numbers = Console.ReadLine().Split(" ").Select(int.Parse).ToList();
            string input = string.Empty;

            while ((input = Console.ReadLine()) != "END")
            {
                string[] commands = input.Split(" ").ToArray();
                if (commands[0] == "Change")
                {
                    int paintingNumber = int.Parse(commands[1]);
                    int changedNumber = int.Parse(commands[2]);
                    if (numbers.Contains(paintingNumber))
                    {
                        int indexOfPaint = numbers.IndexOf(paintingNumber);
                        
                        numbers.RemoveAt(indexOfPaint);
                        numbers.Insert(indexOfPaint, changedNumber);
                        
                    }
                }
                if (commands[0] == "Hide")
                {
                    int paintingNumber = int.Parse(commands[1]);
                    if (numbers.Contains(paintingNumber))
                    {
                        numbers.Remove(paintingNumber);
                    }
                }
                if (commands[0] == "Switch")
                {
                    int paintingNumber1 = int.Parse(commands[1]);
                    int paintingNumber2 = int.Parse(commands[2]);
                    if(numbers.Contains(paintingNumber1) && numbers.Contains(paintingNumber2))
                    {
                        int indexOf1 = numbers.IndexOf(paintingNumber1);
                        int indexOf2 = numbers.IndexOf(paintingNumber2);
                        
                        numbers.Remove(paintingNumber1);
                        numbers.Insert(indexOf1, paintingNumber2);
                        numbers.Remove(paintingNumber2);
                        numbers.Insert(indexOf2, paintingNumber1);

                    }

                }
                if (commands[0] == "Insert")
                {
                    int place = int.Parse(commands[1])+1;
                    int paintingNumber = int.Parse(commands[2]);
                    if (numbers.Count() - place > 0)
                    {
                        numbers.Insert(place, paintingNumber);
                    }
                }
                if (commands[0] == "Reverse")
                {
                    numbers.Reverse();
                }
                
            }
            Console.WriteLine(string.Join(" ", numbers));
        }
    }
}


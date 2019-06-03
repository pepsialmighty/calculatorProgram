# calculatorProgram

using System;


namespace ex1
{
    class Program
    {
        static double a, b, c, d;
        static bool ktSoA, ktSoB, ktSoC, ktSoD;

        static void Main(string[] args)
        {
           
           
            int countDai = 0;
            int countRong = 0;

            char inSide = ' ';
            char outSide = '#';
            Random rand = new Random();
            int dai = 40;
            int rong = 10;
            

            while (countRong <= rong)
            {
                while(countDai <= dai)
                {
                    if(countRong == 0 || countRong == rong || countRong%rong != 0 && countDai%dai == 0)
                    {
                        Console.Write(outSide);
                    }
                    
                    else
                    {
                        Console.Write(inSide);
                        if (countRong == rong / 2 && countDai == 2)
                        {
                            Console.Write("Chuong trinh phuong trinh bac 2");
                           
                        }
                    }
                    countDai++;

                }
                
                countDai = 0;
                countRong++;
                Console.WriteLine();
            }

            
            Console.WriteLine("\n1.Giai phuong trinh bac 1 \n2.Giai phuong trinh bac 2 \n3.Giai phuong trinh bac 3\nMoi ban chon loai phuong trinh :");
            int option = Int32.Parse(Console.ReadLine());




            if (option == 1)
            {
                Console.WriteLine("\nNhap so a");
                ktSoA = Double.TryParse(Console.ReadLine(), out a);
                Console.WriteLine("Nhap so b");
                ktSoB = Double.TryParse(Console.ReadLine(), out b);
            }
            else if (option == 2)
            {
                Console.WriteLine("\nNhap so a");
                ktSoA = Double.TryParse(Console.ReadLine(), out a);
                Console.WriteLine("Nhap so b");
                ktSoB = Double.TryParse(Console.ReadLine(), out b);
                Console.WriteLine("Nhap so c");
                ktSoC = Double.TryParse(Console.ReadLine(), out c);
            }        
            else
            {
                Console.WriteLine("\nNhap so a");
                ktSoA = Double.TryParse(Console.ReadLine(), out a);
                Console.WriteLine("Nhap so b");
                ktSoB = Double.TryParse(Console.ReadLine(), out b);
                Console.WriteLine("Nhap so c");
                ktSoC = Double.TryParse(Console.ReadLine(), out c);
                Console.WriteLine("Nhap so d");
                ktSoD = Double.TryParse(Console.ReadLine(), out d);
            }
             
                    
            

            if (ktSoA == false || ktSoA == false&& ktSoB == false || ktSoA == false && ktSoB == false&& ktSoC == false || ktSoA == false && ktSoB == false && ktSoC == false&&ktSoD == false)
            {
                Console.WriteLine("xin moi nhap lai ");
            }



            else if (option == 1)
            {
                printFisrtRootSolution(a, b);
            }
            else if (option == 2)
            {
                printSquareSolution(a, b, c);
            }
            else
            {
                print3rdRootSolution(a, b, c, d);
            }



            Console.ReadKey();
        }



        static double Delta(double firstNum, double secondNum , double thirdNum)
        {
            return Math.Pow(secondNum,2) - 4 * firstNum * thirdNum;
        }

        static double Solution1(double firstNum, double secondNum, double thirdNum)
        {
            double firstResult;
            return firstResult = (-secondNum + Math.Sqrt(Delta(firstNum, secondNum, thirdNum))) / (2 * firstNum);
        }

        static double Solution2(double firstNum, double secondNum, double thirdNum)
        {
            double secondResult;
            return secondResult = (-secondNum + Math.Sqrt(Delta(firstNum, secondNum, thirdNum))) / (2 * firstNum);
        }

        static void printSquareSolution(double firstNum, double secondNum, double thirdNum)
        {
            Console.WriteLine("phuong trinh can giai la \n[{0}]x^2 + [{1}]x + [{2}] = 0 ", firstNum, secondNum, thirdNum);
            if (Delta( firstNum,secondNum, thirdNum) ==0)
            {
                Console.WriteLine("Nghiem kep cua phuong trinh la {0}",-secondNum/(2*firstNum) );
            }
            else if (firstNum == 0)
            {
                Console.WriteLine("nghiem cua phuong tirnh la {0}", -thirdNum / secondNum);
            }
            else if (Delta(firstNum, secondNum, thirdNum) < 0)
            {
                Console.WriteLine("phuong trinh vo nghiem!");
            }
            else
            {                
                Console.WriteLine("Nghiem 1 la : {0}", Solution1(firstNum, secondNum, thirdNum));
                Console.WriteLine("Nghiem 2 la : {0}", Solution1(firstNum, secondNum, thirdNum));
            }
        }






        static void printFisrtRootSolution(double firstNum, double secondNum)
        {            
                Console.WriteLine("Phuong trinh can giai la [{0}]x + [{1}] = 0",firstNum,secondNum);
                Console.WriteLine("nghiem cua phuong tirnh la {0}", -secondNum/firstNum);
            
        }







        static double Delta3rd(double firstNum, double secondNum, double thirdNum)
        {
            return Math.Pow(secondNum, 2) - 3 * firstNum * thirdNum;
        }

        static double k(double firstNum, double secondNum, double thirdNum, double fourthNum)
        {
            return (9*firstNum*secondNum*thirdNum - 2*Math.Pow(secondNum,3) - 27*Math.Pow(firstNum,2)*d)/ (2 * Math.Sqrt(Math.Abs(Math.Pow(Delta3rd(firstNum,secondNum,thirdNum),3))));
        }

        static void print3rdRootSolution(double firstNum, double secondNum, double thirdNum, double fourthNum)
        {
            Console.WriteLine("Phuong trinh bac 3 can giai la [{0}]x^3 + [{1}]x^2 + [{2}]x + [{3}] = 0");

            if(Delta3rd(firstNum, secondNum, thirdNum) > 0 )
            {
                if(k(firstNum,secondNum,thirdNum,fourthNum) <= 1)
                {
                    double x1, x2, x3;
                    x1 = (2 * Math.Sqrt(Delta3rd(firstNum, secondNum, thirdNum)) * (Math.Acos(k(firstNum, secondNum, thirdNum, fourthNum))/3) - b ) / (3 * firstNum);
                    x2 = (2 * Math.Sqrt(Delta3rd(firstNum, secondNum, thirdNum)) * (Math.Acos(k(firstNum, secondNum, thirdNum, fourthNum))/3 - (2*Math.PI/3)) - b ) / (3 * firstNum);
                    x3 = (2 * Math.Sqrt(Delta3rd(firstNum, secondNum, thirdNum)) * (Math.Acos(k(firstNum, secondNum, thirdNum, fourthNum))/3 + (2*Math.PI/3)) - b ) / (3 * firstNum);

                    Console.WriteLine("Nghiem can tim la \nx1 = {0}\nx2 = {1}\nx3 = {2}",x1,x2,x3);

                }
                else
                {
                    double x;
                    x = (Math.Sqrt(Delta3rd(firstNum, secondNum, thirdNum) * Math.Abs(k(firstNum, secondNum, thirdNum, fourthNum)) / (3 * firstNum * k(firstNum, secondNum, thirdNum, fourthNum)))) * (Math.Pow(Math.Abs(k(firstNum, secondNum, thirdNum, fourthNum)) + Math.Sqrt(Math.Pow(k(firstNum, secondNum, thirdNum, fourthNum), 2) - 1), 1 / 3) + Math.Pow(Math.Abs(k(firstNum, secondNum, thirdNum, fourthNum)) - Math.Sqrt(Math.Pow(k(firstNum, secondNum, thirdNum, fourthNum), 2) - 1), 1 / 3)) - secondNum/(3*firstNum);

                    Console.WriteLine("Nghiem can tim la \nx = {0}",x);

                }
            }
            else if(k(firstNum, secondNum, thirdNum, fourthNum) == 0)
            {
                double x;
                x = (-secondNum + Math.Pow(Math.Pow(secondNum, 3) - 27 * Math.Pow(firstNum, 2) * fourthNum, 1 / 3)) / 3*firstNum;

                Console.WriteLine("Nghiem can tim la \nx = {0}", x);

            }
            else
            {
                double x;
                x = (Math.Sqrt(Delta3rd(firstNum, secondNum, thirdNum)/ (3 * firstNum * k(firstNum, secondNum, thirdNum, fourthNum)))) * (Math.Pow(Math.Abs(k(firstNum, secondNum, thirdNum, fourthNum)) + Math.Sqrt(Math.Pow(k(firstNum, secondNum, thirdNum, fourthNum), 2) - 1), 1 / 3) + Math.Pow(Math.Abs(k(firstNum, secondNum, thirdNum, fourthNum)) - Math.Sqrt(Math.Pow(k(firstNum, secondNum, thirdNum, fourthNum), 2) - 1), 1 / 3)) - secondNum / (3 * firstNum);

                Console.WriteLine("Nghiem can tim la \nx = {0}", x);

            }
        }
    }
}


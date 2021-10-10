# Тут можна скопіювати код

using System;

namespace figures
{
    class Figures
    {
        Random random = new Random();
        public double a;
        public double b;
        public double c;
        public double d;
        public string white = "бiлий";
        public string red = "червоний";
        public string green = "зелений";
        public string blue = "синiй";
        public string purple = "фiолетовий";
        public Figures(double a1) { a = a1;}
        public Figures(double a1, double b1, double c1) { a = a1; b = b1; c = c1; }
        public Figures(double a1, double b1, double c1, double d1) { a = a1; b = b1; c = c1; d=d1;}
        public Figures() { }
        public void triangle()
        {
            double P_triangle = a + b + c;
            double S_triangle = Math.Sqrt(P_triangle / 2*(P_triangle/2-a)*(P_triangle/2-b) *(P_triangle/2-c));
            Figures color = new Figures();
            Console.WriteLine("Фiгура: трикутник, площа: "+ Math.Round(S_triangle) + " кв.од, периметр: "+ P_triangle+ ", сторони: " + a+" од., "+b+" од., " + c+ ", од., "+"колiр: "+color.color());
        }
        public void trapezoid()//b d основа a b стороны
        {
            double Middle_tr = (b + d) / 2;
            double ln = d - b; 
            double k = (ln * ln) + (a * a) - (c * c);
            k = k / (2 * ln);
            ln = (a * a)-k*k;
            k = Math.Sqrt(ln);
            double S_trapezoid = Middle_tr * k;
            Figures color = new Figures();
            double P_trapezoid = a + b + c + d;
            double H_tr = S_trapezoid / Middle_tr;
            Console.WriteLine("Фiгура: трапецiя, площа: " + Math.Round(S_trapezoid) + " кв.од, периметр: " + P_trapezoid + "од., середня лiнiя: "+Middle_tr+"од., висота: " + Math.Round(H_tr) + ", сторони: " + a + " од., " + b + " од., " + c + ", од., " + d+" од., " + "колiр: " + color.color());
        }
        public void circle()
        {
            Figures color = new Figures();
            double D_cl = 2 * a;
            double S_cl = Math.PI * Math.Pow(a, 2);
            double C_cl = 2 * Math.PI * a;
            Console.WriteLine("Фiгура: коло, площа: " + Math.Round(S_cl) + " кв.од, радiус: " +a + " од., дiаметр: " + D_cl + " од., довжина кола:" + Math.Round(C_cl) + " од., колiр: " + color.color());
        }
        public void square()
        {
            Figures color = new Figures();
            double S_sq = a * a;
            double P_sq = a * 4;
            double d_sq = Math.Sqrt(2 * S_sq);
            Console.WriteLine("Фiгура: квадрат, площа: " + Math.Round(S_sq) + " кв.од, сторона: " + a + " од., периметр: " + P_sq + " од., дiагональ:" + Math.Round(d_sq) + " од., колiр: " + color.color());
        }
        public string color()
        {
            int rdm = random.Next(1, 6);
            string color = "color";
            switch (rdm)
            {
                case 1:
                    color = white; break;
                case 2:
                    color = red; break;
                case 3:
                    color = green; break;
                case 4:
                    color = blue; break;
                case 5:
                    color = purple; break;
            }
            return color;
        }
    }
    class Program
    {
        static void Main(string[] args)
        {
            Random rnd = new Random();
            int value = rnd.Next(2, 7);
            for(int i = 0; i < value; i++)
            {
                double a;
                double b;
                double c;
                double d;
                int figure_num = rnd.Next(1, 5);
                switch (figure_num)
                {
                    case 1: //метод треугольника
                        do
                        {
                            a = rnd.Next(1, 25);
                            b = rnd.Next(1, 25);
                            c = rnd.Next(1, 25);
                        }
                        while (a + b <= c || a + c <= b || b + c <= a);
                        Figures triangle = new Figures(a, b, c);
                        triangle.triangle();
                        ; break;
                    case 2: //метод трапеции 
                        double koef = rnd.Next(1, 3);
                        double koef1 = rnd.Next(4, 7);
                        do
                        {
                            a = rnd.Next(1, 25);
                            b = rnd.Next(1, 25);
                            c = a + koef;
                            d = b + koef1;
                        }
                        while (a - b > 3 || b - a > 3);
                        Figures trapezoid = new Figures(a, b, c, d);
                        trapezoid.trapezoid();
                        ; break;
                    case 3: //метод круга
                        a = rnd.Next(1, 25);//r
                        Figures circle = new Figures(a);
                        circle.circle(); ; break;
                    case 4: //метод квадрата
                        a = rnd.Next(1, 25);
                        Figures square = new Figures(a);
                        square.square() ; break;
                }
            }
        }
    }
}

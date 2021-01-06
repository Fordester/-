	//#include “stdafx.h”
	#include <iostream>
	#include <fstream>

	using namespace std;
	double G(double a, double b) {
		if (a >= 0) {
			return log(1 + 2 * a + b * b) + 1;
		}
		else {
			return log(1 + a * a + b * b) - 1;
		}
	}
	double F(double a, double b)
	{
		return sqrt(2 + sin(a + b)) + sqrt(2 - cos(a + b));
	}
	double fun(double a, double b)
	{
		return sqrt(abs(a - b));
	}

	void liniya(ofstream& f)
	{
		int i;
		for (i = 0; i < 35; i++)
			f << "*";
		f << endl;
	}

	void emptline(ofstream& f) {
		for (int i = 0; i < 2; i++)
			f << "*                ";
		f << "*" << endl;
	}

	int main()
	{
		ifstream in("input.txt");
		if (in.is_open())
		{
			double a0, b0, e;
			int n;
			in >> a0 >> b0 >> n >> e;
			double* a = new double[n];
			double* b = new double[n];
			a[0] = a0;
			b[0] = b0;
			for (int i = 1; i < n; i++)
			{
				a[i] = F(a[i - 1], b[i - 1]);
				b[i] = G(a[i - 1], b[i - 1]);
			}
			ofstream out("output.txt"); // создаём объект класса ofstream для записи и связываем его с файлом output.txt
			liniya(out);
			for (int i = 0; i < n; i++)
			{
				emptline(out);
				bool isCorrect = false;
				for (int j = 0; j < n; j++) {
					if (fun(a[i], b[j]) < e)
					{
						isCorrect = true;
					}
				}
				if (isCorrect)
				{
					out << "*" << "\t" << "a[" << i << "]\t     *   " << "\t" << a[i] << "\t  *" << endl;
					emptline(out);
					liniya(out);
				}
			}

			out.close();
			delete[] a;
			delete[] b;
			in.close();//под конец закроем файла
		}
		else
		{
			cout << "File input.txt not found."; //Если открытие файла прошло не успешно
			system("pause");
			exit(-1);
		}
		system("pause");
		return 0;
    }

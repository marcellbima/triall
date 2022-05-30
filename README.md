# triall
#include <iostream> // library input output
#include <conio.h>  // _getch(), _getche(), clrscr()
#include <ctime> // menampilkan waktu dan tanggal
#include <stdlib.h> //operasi pembanding dan operasi konversi
#include <string> //berfungsi untuk melakukan manipulasi string
#include <fstream> // output teks

using namespace std;

int  pilihan();  // deklarasi
void cekdata();
void masukandata();
void tampilkandata();
void ubahdata();
void hapusdata();
void admin();

int main()
{
	int pilih, no, totalharga, harga, beli, total, kembalian, bayar, a, b, harga1[50], harga2[50], jml[50];
	string nama[50];
	string produk;
	char ngulang;
	// Tampilan Awal / Home
pertama:
	cout << endl;
	cout << "################################################################" << endl;
	cout << "#--------------------------------------------------------------#" << endl;
	cout << "#                        RASING MART                           #" << endl;
	cout << "#                 JL. In AJA Dulu no. 1 YaKamuLah              #" << endl;
	cout << "#--------------------------------------------------------------#" << endl;
	cout << "################################################################" << endl;
	cout << endl;
	cout << "Menu" << endl;
	cout << "[1] Admin " << endl;
	cout << "[2] Pembayaran " << endl;
	cout << "[3] Keluar" << endl;
	cout << endl << endl;	
	cout << "Masukan Pilihan : ";
	cin >> pilih; // input pilihan menu   

	// pilihan 1. Masuk sebagai admin
	if (pilih == 1)
	{
		string pass;
		char ch, go;
		system("cls");
		cout << "-------------------------" << endl;
		cout << "Anda Login sebagai Admin" << endl;
		cout << "-------------------------" << endl << endl;
		cout << "Masukan Password = ";
		ch = _getch();
		pass += ch;
		cout << "x";
		no = 1;
		while (no != 8)
		{
			ch = _getch();
			if (ch == '\n')
			{
				break;
			}
			cout << " x";
			pass += ch;
			no++;
		}
		if (pass == "123456789") // password 1
		{
			cout << "\nPassword Anda Benar\n";
			cout << "Tekan Enter Untuk Melanjutkan";
			go = _getch();
		}
		else if (pass == "20202031") // password 2
		{
			cout << "\nPassword Anda Benar\n";
			cout << "Tekan Enter Untuk Melanjutkan";
			go = _getch();
		}
		else if (pass == "20202022") // password 3
		{
			cout << "\nPassword Anda Benar\n";
			cout << "Tekan Enter Untuk Melanjutkan";
			go = _getch();
		}
		else
		{
			cout << endl;
			cout << "Password Anda Salah" << endl;
			cout << "Tekan Enter Untuk Melanjutkan";
			go = _getch();
			system("cls");
			goto pertama;
		}
		admin(); // program admin 
		system("cls");
		goto pertama;
	}

	// pilihan 2. Pembayaran
	else if (pilih == 2)
	{
		totalharga = 0;
		b = 0;
	ulang:
		system("cls");
		cout << "-----------------------" << endl;
		cout << "Menu Pembayaran" << endl;
		cout << "-----------------------" << endl << endl;
		cout << "Masukan Produk : ";
		cin >> produk;
		nama[b] = produk;
		fstream data;
		string isi;
		data.open("data.txt", ios::in);

		do // pengulangan barang yang dibeli
		{
			getline(data, isi);
			getline(data, isi);
		} while (isi != produk);
		getline(data, isi);
		cout << " " << endl;
		cout << "Harga Produk :  " << isi << endl;
		data.close();
		harga = atoi(isi.c_str());
		harga1[b] = harga;
		cout << endl;
		cout << "Jumlah : ";
		cin >> beli;
		jml[b] = beli;
		cout << endl;
		total = harga * beli;
		harga2[b] = total;
		b++;
		totalharga += total;

	awal2:
		cout << " " << endl; // pilihan tambah produk atau tidak
		cout << "Tambah Produk ? (Y/N): ";
		cin >> ngulang;

		if (ngulang == 'y')
		{
			goto ulang;
		}
		else if (ngulang == 'n')
		{
			cout << endl;
			cout << "------------------------" << endl;
			cout << "Barang Yang Dibeli" << endl;
			cout << "------------------------" << endl;
			for (a = 0; a<b; a++)
			{
				cout << nama[a] << "\t" << jml[a] << "\t" << harga1[a] << "\t" << harga2[a] << endl;
			}
			cout << " " << endl;
			cout << "Total Harga : Rp.  " << totalharga << endl;
			cout << endl;
			cout << "Bayar       : Rp.  ";
			cin >> bayar;
			cout << endl;
			kembalian = bayar - totalharga;
			// menampilkan waktu dan tanggal pada nota
			
			//time_t t;
			//time(&t);
			//char *tanggal = ctime(&t);
			system("cls");

			// Output Nota
			cout << "--------------------------------------------------------------" << endl;
			cout << "                                                              " << endl;
			cout << "                        RASING MART                           " << endl;
			cout << "                 JL. In AJA Dulu no. 1 YaKamuLah              " << endl;
			cout << "                                                              " << endl;
			cout << "--------------------------------------------------------------" << endl;
			//cout << "                       " << tanggal << "						 " << endl;
			cout << "--------------------------------------------------------------" << endl;
			cout << "Nama" <<"\t"<< "Jumlah Harga" << "\t" << "Total" << endl;

			for (a = 0; a<b; a++)
			{
				cout << nama[a] << "\t" << jml[a] << "\t" << harga1[a] << "\t" << harga2[a] << endl;
			}

			cout << endl;
			cout << "-----------------------------------------------------------------"       << endl;
			cout << "   " << "\t" << "\t" << "Total     : Rp. " << "\t" << "\t" << totalharga << endl;
			cout << "   " << "\t" << "\t" << "Bayar     : Rp. " << "\t" << "\t" << bayar      << endl;
			cout << "   " << "\t" << "\t" << "Kembali   : Rp. " << "\t" << kembalian          << endl;
			cout << "-----------------------------------------------------------------" << endl << endl;
			cout << "                Terima Kasih Telah Membeli Di Toko Kami          " << endl;
			cout << "                   Customer Service : 081326224984               " << endl;
			cout << "                Kepuasan Pelanggan adalah Prioritas Kami         " << endl;
			cout << "                      Kunjungi www.RasingMart.com                " << endl;
			cout << endl;

			fstream data3; // menampilkan .txt struk pembelian
			data3.open("struk.txt", ios::trunc | ios::out);
			data3 << endl << endl;
			data3 << "===================================================" << endl;
			data3 << "                   Rasing MART " << endl;
			data3 << "      JL. In AJA Dulu no. 1 YaKamuLah  " << endl;
			data3 << "===================================================" << endl;
			//data3 << "                   " << tanggal << endl;
			data3 << "Nama       Jumlah        Harga          Total "      << endl;

			for (a = 0; a<b; a++)
			{
				data3 << nama[a] << "\t" << "\t" << jml[a] << "\t" << harga1[a] << "\t" << "\t" << harga2[a] << endl;
			}
			data3 << "----------------------------------------------" << endl;
			data3 << endl;
			data3 << "\t" << "\t" << "\t" << "Total    Rp. " << "\t"  << totalharga << endl;
			data3 << "\t" << "\t" << "\t" << "Tunai    Rp. " << "\t"  << bayar << endl;
			data3 << "\t" << "\t" << "\t" << "Kembali  Rp. " << "\t"  << kembalian << endl;
			data3 << endl; 
			data3 << "----------------------------------------------" << endl << endl;
			data3 << "   Terima Kasih Telah Membeli Di Toko Kami    " << endl;
			data3 << "     Customer Service : 081326224984          " << endl;
			data3 << "   Kepuasan Pelanggan adalah Prioritas Kami   " << endl;
			data3 << "         Kunjungi www.RasingMart.com          " << endl << endl;
			data3 << "----------------------------------------------" << endl << endl;
			data3.close();
			a = _getch();
			system("cls");
			goto pertama;
		}
		else { goto awal2; }
	}
	else if (pilih == 3) { goto akhir; }
	else
	{
		system("cls");
		goto pertama;
	}
akhir:
	cout << "Terima Kasih" << endl;
	return 0;
}

int pilihan()
{
	int pilih;
	system("cls");
	cout << "--------------------------" << endl;
	cout << "Anda Login Sebagai Admin" << endl;
	cout << "--------------------------" << endl;
	cout << endl;
	cout << "Menu : " << endl;
	cout << "[1] Tambah Produk" << endl;
	cout << "[2] List Produk" << endl;
	cout << "[3] Ubah Produk" << endl;
	cout << "[4] Hapus Produk" << endl;
	cout << "[5] Keluar" << endl;
	cout << " " << endl;
	cout << "Masukan Pilihan : "; 
	cin >> pilih;
	return pilih;
}

void masukandata() // input nama produk dan harga
{
	fstream data;
	char lanjut;
	string isi;
	do
	{
		data.open("data.txt", ios::out | ios::app); // mengubah data inputan menjadi .txt
		cout << endl;
		getline(cin, isi);
		cout << "Nama Produk:";
		getline(cin, isi);
		data << '\n' + isi;
		cout << "Harga Produk:";
		getline(cin, isi);
		data << '\n' + isi;
		data.close();

	u:
		cout << "Apakah Ingin Menambahkan (y,n) ";
		cin >> lanjut;
	} while (lanjut == 'y');

	if (lanjut != 'y'&&lanjut != 'n')
	{
		cout << "Masukan Pilihan Yang Tepat";
		cout << endl;
		goto u;
	}
}

void tampilkandata() // menampilkan data .txt yang sudah diinputkan 
{
	fstream data;
	string isi;
	int no;
	data.open("data.txt", ios::in);
	getline(data, isi);
	no = 1;
	cout << "No " << '\t' << '\t';
	cout << "Produk: " << '\t';
	cout << "Harga: " << endl;
	do
	{
		getline(data, isi);
		cout << no++ << '\t' << '\t';
		cout << isi << '\t' << '\t';
		getline(data, isi);
		cout << isi << endl;
	} while (!data.eof());
	data.close();
}

void ubahdata() // mengubah data produk yang sudah diinput
{
	fstream data, data2;
	int no, i;
	string isi;
	cout << "Pilih Barang : "; cin >> no;
	data2.open("data2.txt", ios::trunc | ios::out);
	data.open("data.txt", ios::in);
	getline(data, isi);
	for (i = 1; i<no; i++)
	{
		getline(data, isi);
		data2 << '\n' + isi;
		getline(data, isi);
		data2 << '\n' + isi;
	}
	cout << "No " << '\t' << '\t';
	cout << "Produk: " << '\t';
	cout << "Harga: " << endl;
	getline(data, isi);
	cout << no++ << '\t' << '\t';
	cout << isi << '\t' << '\t';
	getline(data, isi);
	cout << isi << endl;

	cout << "Nama Produk   : ";
	getline(cin, isi);
	getline(cin, isi);
	data2 << '\n' + isi;
	cout << "Harga Produk :";
	getline(cin, isi);
	data2 << '\n' + isi;

	while (!data.eof())
	{
		getline(data, isi);
		data2 << '\n' + isi;
		getline(data, isi);
		data2 << '\n' + isi;
	}
	data2.close();
	data.close();

	data2.open("data2.txt", ios::in);
	data.open("data.txt", ios::trunc | ios::out);
	getline(data2, isi);

	do
	{
		getline(data2, isi);
		data << '\n' + isi;
		getline(data2, isi);
		data << '\n' + isi;
	} while (!data2.eof());

	data2.close();
	data.close();
}

void hapusdata() // menghapus data yang sudah diinput
{
	fstream data, data2;
	string isi;
	int no, i;
	cout << "Pilih Barang : "; cin >> no;
	data2.open("data2.txt", ios::trunc | ios::out);
	data.open("data.txt", ios::in);
	getline(data, isi);

	for (i = 1; i<no; i++)
	{
		getline(data, isi);
		data2 << '\n' + isi;
		getline(data, isi);
		data2 << '\n' + isi;
	}
	cout << endl;
	cout << "No    " << '\t' << '\t';
	cout << "Produk: " << '\t';
	cout << "Harga : " << endl;
	getline(data, isi);
	cout << no++ << '\t' << '\t';
	cout << isi << '\t' << '\t';
	getline(data, isi);
	cout << isi << endl;

	while (!data.eof())
	{
		getline(data, isi);
		data2 << '\n' + isi;
		getline(data, isi);
		data2 << '\n' + isi;
	}

	data2.close();
	data.close();

	data2.open("data2.txt", ios::in);
	data.open("data.txt", ios::trunc | ios::out);
	getline(data2, isi);
	do
	{
		getline(data2, isi);
		data << '\n' + isi;
		getline(data2, isi);
		data << '\n' + isi;
	} while (!data2.eof());

	data2.close();
	data.close();

	cout << "Produk telah dihapus" << endl;
}

void admin() // program masuk ke admin setelah dimasukan password 
{
	fstream data, data2;

ulang:

	int pilih = pilihan();
	int no;
	char ulang;
	string salur, isi, datane;

	while (pilih != 5)
	{
		switch (pilih)
		{
		case 1:
			system("cls");
			cout << "-------------------" << endl;
			cout << "   Tambah Produk" << endl;
			cout << "-------------------" << endl;
			masukandata();
			no = _getch();
			goto ulang;
			break;

		case 2:
			system("cls");
			cout << "-------------------" << endl;
			cout << "     List Barang" << endl;
			cout << "-------------------" << endl;
			tampilkandata();
			no = _getch();
			goto ulang;
			break;

		case 3:
			system("cls");
			cout << "-------------------" << endl;
			cout << "     Ubah Barang" << endl;
			cout << "-------------------" << endl;
			tampilkandata();
			ubahdata();
			no = _getch();
			goto ulang;
			break;

		case 4:
			system("cls");
			cout << "-------------------" << endl;
			cout << "     Hapus Data" << endl;
			cout << "-------------------" << endl;
			tampilkandata();
			hapusdata();
			no = _getch();
			goto ulang;
			break;

		default:
			cout << "Pilihan Tidak Di Temukan" << endl;
		maning:
			cout << "Lanjutkan (y,n): ";
			cin >> ulang;
			if (ulang == 'y')
			{
				goto ulang;
			}
			else if (ulang == 'n')
			{
				goto akhir;
			}
			else
			{
				goto maning;
			}
			break;
		}
	}
akhir:
	cout << endl;
}

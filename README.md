#include <iostream>

using namespace std;

int i = 1;
int j = 1;
struct pohon{
    pohon* kanan;
    char data;
    pohon* kiri;
};

pohon* simpul;
pohon* root;
pohon* saatIni;
pohon* helperA;
pohon* helperB;
pohon* alamat[256];

void insialisasi(){
    root = NULL;
}

void simpulBaru(char dataMasukkan){
    simpul = new pohon;
    simpul->data = dataMasukkan;
    simpul->kanan = NULL;
    simpul->kiri = NULL;
}

void simpulAkar(){
    if(root == NULL){
        char dataAnda;
        cout<<"Silahkan masukkan data : ";
        cin>>dataAnda;
        simpulBaru(dataAnda);
        root = simpul;
        alamat[i] = root;
        cout<<"Root terbentuk..."<<endl;
    }else{
        cout<<"Root sudah ada..."<<endl;
    }
}


void tambahSimpul(){
    if(root != NULL){
        int penanda;
        char dataUser;
        penanda = 0;
        while(penanda == 0 && j < 256){
            saatIni = alamat[i];
            if(saatIni->kiri == NULL){
                cout<<"Masukkan data kiri : ";
                cin>>dataUser;
                if(dataUser != '0'){
                    simpulBaru(dataUser);
                    saatIni = alamat[i];
                    saatIni->kiri = simpul;
                    j++; // j = 2
                    alamat[j] = simpul;
                }else{
                    penanda = 1;
                }
            }


            if(penanda == 0){
                cout<<"Masukkan data kanan : ";
                cin>>dataUser; // C
                if(dataUser != '0'){
                    simpulBaru(dataUser);
                    saatIni = alamat[i];
                    saatIni->kanan = simpul;
                    j++;
                    alamat[j] = simpul;
                    i++;
                }else{
                    penanda = 1;
                }
            }

        }
    }

}

void bacaPohon(){
    if(root != NULL){
        int i, n, pencacah;
        i = 1;
        n = 1;
        pencacah = 0;
        cout<<endl;
        while(i <= j){
            saatIni = alamat[i];
            cout<<saatIni->data<<" ";
            pencacah++;
            if(pencacah == n){
                cout<<endl;
                pencacah = 0;
                n = n*2;
            }
            i++;
        }
        cout<<endl;
    }
}

int main()
{
    simpulAkar();
    tambahSimpul();
    bacaPohon();
    tambahSimpul();
    bacaPohon();
    return 0;
}

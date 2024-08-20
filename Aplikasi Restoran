from tkinter import *
from tkinter import messagebox
import csv

fileCsv = 'UAP.csv'
headerCsv = ['Rincian', 'Total Harga', 'Uang Bayar', 'Kembalian', 'Tanggal']
app = Tk()
app.title('Sistem Menejemen Restoran Dimas')

Nasi = StringVar()
AyamGRG = StringVar()
AyamBKR = StringVar()
TahuTLR = StringVar()
Tahu = StringVar()
Tempe = StringVar()
tekstotal = StringVar()
teksUang = StringVar()
total = 0

# buat function
def totalbeli():
    global Nasi, AyamGRG, AyamBKR, TahuTLR, Tahu, Tempe, total
    hNasi = int(Nasi.get()) * 10000
    hAGoreng = int(AyamGRG.get()) * 15000
    hABakar = int(AyamBKR.get()) * 20000
    hTTelor = int(TahuTLR.get()) * 10000
    hTahu = int(TahuTLR.get()) * 5000
    hTempe = int(Tempe.get()) * 5000
    total = hNasi + hAGoreng + hABakar + hTTelor + hTahu + hTempe
    tekstotal.set(str(total))

def kembalian():
    global total
    uang = int(teksUang.get())

    if uang >= total:
        kembalian = uang - total
        messagebox.showinfo(message='Kembalian kamu sebesr {} \n Terimakasih Telah Berbelanja'.format(str(kembalian)))
    else:
        messagebox.showerror(message='maaf uang kamu kurang')

def clear():
    Nasi.set('0'); AyamGRG.set('0'); AyamBKR.set('0'); TahuTLR.set('0')
    Tahu.set('0'); Tempe.set('0'); tekstotal.set('0'); teksUang.set('0')

def addData(data):
    for item in data.values():
        if not item:
            messagebox.showerror('Error','Data tidak boleh kosong')
            return
    with open(fileCsv, 'a+') as files:
        reading = csv.DictReader(files, headerCsv)
        files.seek(0)
        for item in reading:
            if(item['Rincian'] == data['Rinciam']):

                return
        writer = csv.DictWriter(files, headerCsv)
        writer.writerow(data)

app.geometry('550x550')

Label(app, text='Masukan uang anda', font='arial 12 ').place(x=100,y=360)
Label(app, text='Menu - UAP PEMLAN', font='arial 18 bold').place(x=150,y=30)

Label(app, text='Nasi - Rp.10.000', font='arial 12 bold').place(x=100,y=100)
Label(app, text='Ayam Goreng - Rp.15.000', font='arial 12 bold').place(x=100,y=140)
Label(app, text='Ayam Bakar - Rp.20.000', font='arial 12 bold').place(x=100,y=180)
Label(app, text='Tahu Telur - Rp.10.000', font='arial 12 bold').place(x=100,y=220)
Label(app, text='Tahu - Rp.5.000', font='arial 12 bold').place(x=100,y=260)
Label(app, text='Tempe -  Rp.5.000', font='arial 12 bold').place(x=100,y=300)

Spinbox(app, from_=0, to=100, width=4, textvariable=Nasi, command=totalbeli).place(x=400,y=100)
Spinbox(app, from_=0, to=100, width=4, textvariable=AyamGRG, command=totalbeli).place(x=400,y=140)
Spinbox(app, from_=0, to=100, width=4, textvariable=AyamBKR, command=totalbeli).place(x=400,y=180)
Spinbox(app, from_=0, to=100, width=4, textvariable=TahuTLR, command=totalbeli).place(x=400,y=220)
Spinbox(app, from_=0, to=100, width=4, textvariable=Tahu, command=totalbeli).place(x=400,y=260)
Spinbox(app, from_=0, to=100, width=4, textvariable=Tempe, command=totalbeli).place(x=400,y=300)

Entry(app, textvariable=teksUang).place(x=100,y=390)

Label(app, text='Rp. ', font='arial 12 bold').place(x=350,y=340)
Label(app, textvariable=tekstotal, font='arial 12 bold').place(x=380,y=340)

Button(app, text='Total', foreground='white', bg='#36ae7c', width=10, command=kembalian).place(x=100,y=440)
Button(app, text='Hapus', foreground='white', bg='#ff1e1e', width=10, command=clear).place(x=250,y=440)

app.mainloop()

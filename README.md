# kalkulator-pajak-tahunan
impor  jawa . menggunakan . Pemindai ;
impor  jawa . teks . Format Angka ;
impor  jawa . menggunakan . Lokal ;

 Aplikasi kelas  publik {
    public  static  void  main ( String [] args ) {
         Masukan pemindai = Pemindai baru  ( System.in ) ; _
        NumberFormat  nf = NumberFormat . getInstance ( Lokal baru  ( "id" , "id" ));

        Sistem . keluar . println ();
        Sistem . keluar . print ( "Masukan penghasilan bersih (Tahunan): " );
        double  penghasilanBersih = input . berikutnyaGanda ();

        Sistem . keluar . print ( "Sudah menikah (ya/tidak)?: " );
        boolean  sudahMenikah = masukan . selanjutnya (). rapikan (). sama dengan ( "ya" );

        // jika sudah menikah, cek apakah punya anak
        int  jumlahAnak = 0 ;
        if ( sudahMenikah ){
            Sistem . keluar . print ( "Masukan jumlah anak: " );
            jumlahAnak = masukan . nextInt ();
        }

        double  penghasilanTidakKenaPajak = hitungPTKP ( penghasilanBersih , sudahMenikah , jumlahAnak );
        if ( penghasilanBersih < penghasilanTidakKenaPajak ){
            Sistem . keluar . println ( "Kamu bebas pajak" );
            masukan . tutup ();
            kembali ;
        }

        double  penghasilanKenaPajak = penghasilanBersih -PenghasilanTidakKenaPajak ; _
        double  pajakTahunan = hitungPPH ( penghasilanKenaPajak );
        Sistem . keluar . println ();
        Sistem . keluar . println ( "Status: " + ( sudahMenikah ? "Menikah" : "Belum menikah" ));
        if ( sudahMenikah ){
            Sistem . keluar . println ( "Jumlah anak: " + jumlahAnak + " anak" );
        }
        Sistem . keluar . println ( "Penghasilan bersih: " + nf .format ( penghasilanBersih ) );
        Sistem . keluar . println ( "Penghasilan tidak kena pajak: " + nf.format ( penghasilanTidakKenaPajak ) ) ;
        Sistem . keluar . println ( "Penghasilan kena pajak: " + nf .format ( penghasilanKenaPajak ) );
        Sistem . keluar . println ( " Pajak tahunan: " + nf .format ( pajakTahunan ));
        Sistem . keluar . println ( " Pajak perbulan: " + nf .format ( pajakTahunan / 12 ));
        masukan . tutup ();
    }

    // method untuk menghitung penghasilan tidak kena pajak
    private  static  double  hitungPTKP ( double  penghasilanBersih , boolean  statusNikah , int  jumlahAnak ){
        double  wajibPajak = 54000000 ;
        // wajib pajak pribadi
        if (! statusNikah ) return  wajibPajak ;

        // wajib pajak yang sudah menikah ditambah 4.5jt
        wajibPajak += 4500000 ;

        // maksimum anak yang dihitung wajib pajak adalah 3
        if ( jumlahAnak > 3 ){
            jumlah Anak = 3 ;
        }
// hitung tambahan wajib pajak 4.5jt per anak, maks 3 anak
        wajibPajak += jumlahAnak * 4500000 ;

        kembali  wajibPajak ;
    }

    // method untuk menghitung pajak penghasilan tahunan
    private  static  double  hitungPPH ( double  penghasilanKenaPajak ){
         pph ganda = 0 ;
        double  sisa = penghasilanKenaPajak ;

        // golongan pertama
        ganda  golonganPertama = 50_000_000 ;
        if ( penghasilKenaPajak <= golonganPertama ){
            pph += penghasilanKenaPajak * 0.05 ;
            mengembalikan  pph ;
        }
        pph += golonganPertama * 0,05 ;
        sisa -= golonganPertama ;

        // gologan kedua
        double  golonganKedua = 250_000_000 - golonganPertama ;
        if ( sisa <= golonganKedua ){
            pph += sisa * 0,15 ;
            mengembalikan  pph ;
        }
        pph += golonganKedua * 0.15 ;
        sisa -= golonganKedua ;

        //golongan ketiga
        double  golonganKetiga = 500_000_000 - golonganKedua ;
        if ( sisa <= golonganKetiga ){
            pph += sisa * 0,25 ;
            mengembalikan  pph ;
        }
        pph += golonganKetiga * 0,25 ;
        sisa -= golonganKetiga ;

        // golongan keempat
        if ( sisa > 0 ) {
            pph += sisa * 0,5 ;
        }

        mengembalikan  pph ;
    }

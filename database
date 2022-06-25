package com.example.majujaya.helper;



import android.content.Context;
import android.database.Cursor;
import android.database.sqlite.SQLiteOpenHelper;
import android.database.sqlite.SQLiteDatabase;

import java.util.ArrayList;
import java.util.HashMap;

public class Database extends SQLiteOpenHelper {

    private static final int DATABASE_VERSION = 1;
    static final String DATABASE_NAME = "majujaya";

    public Database(Context context){
        super(context, DATABASE_NAME, null,DATABASE_VERSION);

    }


    //oncreate Hanya sekali dipanggil
    @Override
    public void onCreate(SQLiteDatabase db) {
        final String SQL_CREATE_TABLE = "CREATE TABLE barang (id INTEGER PRIMARY KEY autoincrement,nama TEXT NOT NULL, jumlah INTEGER NOT NULL)";
        db.execSQL(SQL_CREATE_TABLE);



    }
    //onupgrade Hanya jika diubah

    @Override
    public void onUpgrade(SQLiteDatabase db, int oldVersion, int newVersion) {
        db.execSQL("DROP TABLE IF EXISTS barang");
        onCreate(db);

    }
    //menampilkan semua data
    public ArrayList<HashMap<String, String>> getAll(){
        ArrayList<HashMap<String, String>> List = new ArrayList<HashMap<String, String>>();
        String QUERY = "SELECT * FROM barang";
        SQLiteDatabase database = this.getReadableDatabase();
        Cursor cursor = database.rawQuery(QUERY,null);
        if(cursor.moveToFirst()){
            do{
                HashMap<String,String> map = new HashMap<>();
                map.put("id",cursor.getString(0));
                map.put("nama",cursor.getString(1));
                map.put("jumlah",cursor.getString(2));
                List.add(map);

            }while(cursor.moveToNext());
        }
        cursor.close();
        return List;


    }
    public void insert(String nama,int jumlah){
        SQLiteDatabase database = this.getReadableDatabase();
        String QUERY = "INSERT INTO barang (nama,jumlah) VALUES('"+nama+"','"+jumlah+"')";
        database.execSQL(QUERY);
    }
    public void update(int id,String nama,int jumlah){
        SQLiteDatabase database = this.getReadableDatabase();
        String QUERY = "UPDATE barang set nama = '"+nama+"',jumlah = '"+jumlah+"' WHERE id = "+id;
        database.execSQL(QUERY);

    }
    public void delete(int id){
        SQLiteDatabase database = this.getReadableDatabase();
        String QUERY = "DELETE FROM barang where id = " + id;
        database.execSQL(QUERY);
    }
}

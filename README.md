# AplikasiPengelolaanKontak
 Latihan 3 - Muhammad Fajar Fitrianto (2210010748)
 
 Kelas : 5B NonReg Banjarmasin 

 # Read.Me untuk Aplikasi Pengelolaan Kontak

## Gambaran Umum

Aplikasi **Pengelolaan Kontak** adalah aplikasi berbasis GUI Java Swing yang memungkinkan pengguna untuk mengelola kontak. Pengguna dapat menambah, memperbarui, menghapus, dan mencari kontak. Setiap kontak terdiri dari nama, nomor telepon, dan kategori (misalnya, Teman, Keluarga, Kerja).

## Fitur

- **Tambah Kontak**: Pengguna dapat menambahkan kontak baru dengan memasukkan nama, nomor telepon, dan memilih kategori.
- **Perbarui Kontak**: Pengguna dapat memperbarui detail kontak yang ada dengan memilihnya dari tabel.
- **Hapus Kontak**: Pengguna dapat menghapus kontak yang dipilih (saat ini, fungsionalitas hapus belum diimplementasikan).
- **Fungsi Pencarian**: Pengguna dapat mencari kontak dengan memasukkan teks di kolom pencarian, yang akan memfilter kontak yang ditampilkan secara real-time.
- **Pemilihan Kategori**: Pengguna dapat mengkategorikan kontak ke dalam kategori yang telah ditentukan.

## Persyaratan

- Java Development Kit (JDK) 8 atau lebih tinggi
- IDE yang mendukung Java (misalnya, IntelliJ IDEA, Eclipse)

## Memulai

1. **Clone Repositori**: Unduh atau clone repositori yang berisi kode sumber.

2. **Buka Proyek**: Buka proyek di IDE Java pilihan Anda.

3. **Kompilasi dan Jalankan**: Kompilasi proyek dan jalankan kelas `PengelolaanKontak`.

## Struktur Kode

Kelas utama untuk aplikasi ini adalah `PengelolaanKontak`. Berikut adalah komponen kunci dari kode:

- **Komponen UI**: GUI dibangun menggunakan komponen Swing seperti `JFrame`, `JTable`, `JButton`, `JTextField`, dan `JComboBox`.
- **Model Tabel**: `DefaultTableModel` digunakan untuk mengelola data yang ditampilkan di `JTable`.
- **Penanganan Event**: Listener aksi diimplementasikan untuk tombol guna menangani interaksi pengguna (tambah, perbarui, cari).
- **Penyaringan**: `TableRowSorter` digunakan untuk memfilter kontak yang ditampilkan berdasarkan input pencarian.

## Kode Sumber



```java
/*
 * To change this license header, choose License Headers in Project Properties.
 * To change this template file, choose Tools | Templates
 * and open the template in the editor.
 */
import javax.swing.*;
import javax.swing.table.DefaultTableModel;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.sql.SQLException;
import java.util.List;
import javax.swing.table.TableRowSorter;
import javax.swing.RowFilter;

public class PengelolaanKontak extends javax.swing.JFrame {

    public PengelolaanKontak() {
        initComponents();
    }

    @SuppressWarnings("unchecked")
    private void initComponents() {

        nameField = new javax.swing.JTextField();
        phoneField = new javax.swing.JTextField();
        addButton = new javax.swing.JButton();
        deleteButton = new javax.swing.JButton();
        updateButton = new javax.swing.JButton();
        searchButton = new javax.swing.JButton();
        jScrollPane1 = new javax.swing.JScrollPane();
        JTable1 = new javax.swing.JTable();
        categoryBox = new javax.swing.JComboBox<>();
        searchField = new javax.swing.JTextField();

        setDefaultCloseOperation(javax.swing.WindowConstants.EXIT_ON_CLOSE);

        nameField.setText("Nama");

        phoneField.setText("Telpon");

        addButton.setText("ADD");
        addButton.addActionListener(new java.awt.event.ActionListener() {
            public void actionPerformed(java.awt.event.ActionEvent evt) {
                addButtonActionPerformed(evt);
            }
        });

        deleteButton.setText("DELETE");

        updateButton.setText("UPDATE");
        updateButton.addActionListener(new java.awt.event.ActionListener() {
            public void actionPerformed(java.awt.event.ActionEvent evt) {
                updateButtonActionPerformed(evt);
            }
        });

        searchButton

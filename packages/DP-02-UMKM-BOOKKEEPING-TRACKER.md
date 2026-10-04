# DP-02 — UMKM BOOKKEEPING TRACKER

**Status:** FUNCTIONAL PROTOTYPE / QC-PASSED ENGINE TEST  
**Production engine:** Airtable (Flow 02 — PASS)  
**Base:** MR.ONE TEST - Formula Engine  
**Table:** MR.ONE DP-02 UMKM Bookkeeping Tracker

## Product purpose
A simple bookkeeping tracker for UMKM/small businesses. Users enter date, transaction, income, and expense. Net balance is calculated automatically.

## User workflow
1. Add one transaction per row.
2. Enter date.
3. Enter transaction description.
4. Enter income amount if money comes in.
5. Enter expense amount if money goes out.
6. Leave the opposite amount as zero.
7. Review **Saldo Bersih**; it is calculated automatically as Pemasukan - Pengeluaran.

## Included fields
- Tanggal
- Transaksi
- Kategori
- Pemasukan
- Pengeluaran
- Saldo Bersih (formula)

## QC evidence
Four test transactions were created and read back successfully. Calculated Saldo Bersih values were:
- +Rp150,000
- -Rp35,000
- +Rp100,000
- -Rp50,000

The formula engine therefore produced the expected row-level calculations.

## Important delivery limitation
The Airtable connector available to MR.ONE can create and verify the product structure and data, but it does not expose a verified customer-facing share/template-delivery operation in this session. Therefore **customer delivery/sharing is NOT claimed as PASS**.

## Selling status
**NOT YET READY TO SELL** until a customer delivery mechanism is verified (for example, a working Airtable template/share workflow) and a final customer-facing copy/instructions package is checked.

## Provenance
INPUT: DP-02 product candidate from Workflow 03  
METHOD: Data/Formula/Tracker recipe  
ENGINE: Airtable  
OUTPUT: Functional bookkeeping tracker  
QC: PASS for structure + formula/readback  
DELIVERY: BLOCKED/UNVERIFIED  

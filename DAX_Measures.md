# DAX Measures — OEE Manufacturing Analytics

This document contains the DAX measures and calculated columns used in the OEE Manufacturing Analytics Power BI solution.

---

## 1. OEE Calculations

### OEE %

```DAX
OEE % = 
[Availability %] * [Performance %] * [Quality %]
```

### OEE Loss

```DAX
OEE_loss = 1 - [OEE %]
```

### Current OEE

```DAX
CURRENT_OEE = [OEE %]
```

### OEE Visible

```DAX
OEE_Visible = 
IF(
    [Filter_Selected] = 1,
    [OEE %],
    BLANK()
)
```

---

## 2. Availability Calculations

### Availability %

```DAX
Availability % = 
DIVIDE(
    [Actual_Run_Time],
    [Planned_Time],
    0
)
```

### Availability Loss

```DAX
availability_loss = 1-[Availability %]
```

### Availability Visible

```DAX
Availability_Visible = 
IF(
    [Filter_Selected] = 1,
    [Availability %],
    BLANK()
)
```

### Actual Run Time

```DAX
Actual_Run_Time = 
SUM('PROD  of the Day'[PROD. Hrs.]) + SUM('PROD  of the Day'[MR Hrs.])
```

### Planned Time

```DAX
Planned_Time = 
SUMX (
    SUMMARIZE (
        'PROD  of the Day',
        'PROD  of the Day'[Date],
        'PROD  of the Day'[Machine],
        'PROD  of the Day'[SHIFT]
    ),
    12
)
```

---

## 3. Performance Calculations

### Performance %

```DAX
Performance % = 
DIVIDE(
    [Total_prod_qty],
    [Planned_Production_Qty],
    0
)
```

### Performance Loss

```DAX
performance_loss = 1 - [Performance %]
```

### Performance Visible

```DAX
Performance_Visible = 
IF(
    [Filter_Selected] = 1,
    [Performance %],
    BLANK()
)
```

### Planned Production Quantity

```DAX
Planned_Production_Qty = 
SUMX(
    'PROD  of the Day',
    'PROD  of the Day'[Rated_Speed_Per_Shift] *
    DIVIDE(
        'PROD  of the Day'[PROD. Hrs.] + 'PROD  of the Day'[MR Hrs.],
        'PROD  of the Day'[Available_Hrs]
    )
)
```

---

## 4. Quality Calculations

### Quality %

```DAX
Quality % = 
DIVIDE(
    [Good_Qty],
    [Total_prod_qty],
    0
)
```

### Quality Loss

```DAX
quality_loss = 1 - [Quality %]
```

### Quality Visible

```DAX
Quality_Visible = 
IF(
    [Filter_Selected] = 1,
    [Quality %],
    BLANK()
)
```

---

## 5. Production Calculations

### Actual Production Quantity

```DAX
Actual_Production_Qty = 
'PROD  of the Day'[Production(Qty.)] + 
'PROD  of the Day'[Wastage(Qty.)]
```

### Actual Production Quantity

```DAX
act_pro_qty = 
SUM('PROD  of the Day'[Actual_Production_Qty])
```

### Good Quantity

```DAX
Good_Qty = 
SUM('PROD  of the Day'[Production(Qty.)])
```

### Total Production Quantity

```DAX
Total_prod_qty = 
SUMX(
    'PROD  of the Day',
    'PROD  of the Day'[Good_Qty] + [Wastage_Qty]
)
```

### Wastage Quantity

```DAX
Wastage_Qty = 
SUM('PROD  of the Day'[Wastage(Qty.)])
```

### Total Production Hours

```DAX
tot_prod_hrs = 
SUM('PROD  of the Day'[PROD. Hrs.])
```

### Total Make Ready Hours

```DAX
total_mr_hrs = 
SUM('PROD  of the Day'[MR Hrs.])
```

---

## 6. Production Visibility Measures

### Actual Production Visible

```DAX
Actual_Prod_Visible = 
IF(
    [Filter_Selected] = 1,
    [Total_prod_qty],
    BLANK()
)
```

### Good Quantity Visible

```DAX
Good_Qty_Visible = 
IF(
    [Filter_Selected] = 1,
    [Good_Qty],
    BLANK()
)
```

### Wastage Visible

```DAX
Wastage_Visible = 
IF(
    [Filter_Selected] = 1,
    [Wastage_Qty],
    BLANK()
)
```

### Productive Hours Visible

```DAX
Productive_Hrs_Visible = 
IF(
    [Filter_Selected] = 1,
    [tot_prod_hrs],
    BLANK()
)
```

### Make Ready Hours Visible

```DAX
Mr_HRS_visible = 
IF(
    [Filter_Selected] = 1,
    [total_mr_hrs],
    BLANK()
)
```

### Non-Productive Hours Visible

```DAX
Non_PRODUCTIVE_hrs_Visible = 
IF(
    [Filter_Selected] = 1,
    [NonProductive_Hrs],
    BLANK()
)
```

---

## 7. Average Production Analysis

### Average Production Per Hour

```DAX
Avg_Production_Per_Hour = 
DIVIDE(
    [Total_prod_qty],
    [Actual_Run_Time],
    0
)
```

### Average Production Per Hour Visible

```DAX
Avg_production_PER_HOUR_Visible = 
IF(
    [Filter_Selected] = 1,
    [Avg_Production_Per_Hour],
    BLANK()
)
```

---

## 8. Make Ready / MR Analysis

### Average MR Per Row

```DAX
Avg_per_MR = 
DIVIDE(
    SUM('PROD  of the Day'[MR Hrs.]),
    COUNTROWS('PROD  of the Day'),
    0
)
```

### Average MR Time Per Row — Minutes

```DAX
Avg_MR_Time_Per_Row_Minutes = 
[Avg_per_MR] * 60
```

### Average MR Time Visible

```DAX
Avg_TIME_MR = 
IF(
    [Filter_Selected] = 1,
    [Avg_MR_Time_Per_Row_Minutes],
    BLANK()
)
```

### Average Time Per MR Visible

```DAX
Avg_TIME_Per_MR_visible = 
IF(
    [Filter_Selected] = 1,
    [Avg_MR_Time_Per_Row_Minutes],
    BLANK()
)
```

### Average MR Per Shift

```DAX
Avg_MR_per_Shift = 
AVERAGEX(
    SUMMARIZE(
        'PROD  of the Day',
        'PROD  of the Day'[Date],
        'PROD  of the Day'[Machine],
        'PROD  of the Day'[SHIFT],
        "ShiftMR", SUM('PROD  of the Day'[MR Hrs.])
    ),
    [ShiftMR]
)
```

### MR Per Production Hour — Weighted

```DAX
MR_per_Prod_Hour_Weighted = 
DIVIDE(
    SUM('PROD  of the Day'[MR Hrs.]),
    SUM('PROD  of the Day'[PROD. Hrs.]),
    0
)
```

---

## 9. Non-Productive Hours

```DAX
NonProductive_Hrs = 
VAR Avail = 
    SUMX(
        SUMMARIZE(
            'PROD  of the Day',
            'PROD  of the Day'[Date],
            'PROD  of the Day'[Machine],
            'PROD  of the Day'[SHIFT]
        ),
        12
    )
VAR Prod =
    SUMX(
        SUMMARIZE(
            'PROD  of the Day',
            'PROD  of the Day'[Date],
            'PROD  of the Day'[Machine],
            'PROD  of the Day'[SHIFT],
            "P", SUM('PROD  of the Day'[PROD. Hrs.])
        ),
        [P]
    )
VAR MR =
    SUMX(
        SUMMARIZE(
            'PROD  of the Day',
            'PROD  of the Day'[Date],
            'PROD  of the Day'[Machine],
            'PROD  of the Day'[SHIFT],
            "M", SUM('PROD  of the Day'[MR Hrs.])
        ),
        [M]
    )
VAR Prod_Cap = IF(Prod > Avail, Avail, Prod)
VAR MR_Cap = IF(MR > (Avail - Prod_Cap), (Avail - Prod_Cap), MR)
VAR Idle = Avail - Prod_Cap - MR_Cap
RETURN
IF(Idle < 0, 0, Idle)
```

---

## 10. Shift and Availability Logic

### Available Hours

```DAX
Available_Hrs = 12
```

### Available Shifts Per Day

```DAX
Available_Shifts_Per_Day = 2
```

### Available Shifts Per Sunday

```DAX
Available_Shifts_Per_Sunday = 1
```

### Total Available Shifts

```DAX
Total_Available_Shifts = 
COUNTROWS(
    DISTINCT('PROD  of the Day'[Date])
) * 2
```

### Dynamic Available Shifts

```DAX
Dynamic_Available_Shifts = 
VAR UniqueDates =
    DISTINCT('PROD  of the Day'[Date])
VAR AddShiftCounts =
    ADDCOLUMNS(
        UniqueDates,
        "ShiftCount",
            IF(
                WEEKDAY([Date],2) = 7,
                1,
                2
            )
    )
RETURN
SUMX(AddShiftCounts, [ShiftCount])
```

### Constant Available Shifts Adjusted

```DAX
Constant_Available_Shifts_Adjusted = 
VAR UniqueDates = 
    DISTINCT('PROD  of the Day'[Date])
VAR AddShiftCounts =
    ADDCOLUMNS(
        UniqueDates,
        "ShiftCount",
            IF(
                WEEKDAY([Date],2) = 7,
                1,
                2
            )
    )
RETURN
SUMX(AddShiftCounts, [ShiftCount])
```

### Available Shifts Based on Date and Shift

```DAX
_Total_Available_Shifts = 
COUNTROWS(
    SUMMARIZE(
        'PROD  of the Day',
        'PROD  of the Day'[Date],
        'PROD  of the Day'[SHIFT]
    )
)
```

### Total Available Shifts With Holidays

```DAX
__Total_Available_Shifts = 
VAR Holidays =
    {
        DATE(2025,10,20),
        DATE(2025,10,21),
        DATE(2025,10,22)
    }
VAR UniqueDates =
    DISTINCT('PROD  of the Day'[Date])
VAR AddShiftCounts =
    ADDCOLUMNS(
        UniqueDates,
        "ShiftCount",
            VAR D = [Date]
            RETURN
                IF(
                    D IN Holidays,
                    0,
                    IF(
                        WEEKDAY(D,2) = 7,
                        1,
                        2
                    )
                )
    )
RETURN
SUMX(AddShiftCounts, [ShiftCount])
```

### Production Per Shift

```DAX
Production_Per_Shift = 
DIVIDE(
    [act_pro_qty],
    [_Total_Available_Shifts],
    0
)
```

### Production Per Shift — All Days

```DAX
Production_Per_Shift_by_all_day = 
DIVIDE(
    [Total_prod_qty],
    [_Total_Available_Shifts],
    0
)
```

---

## 11. Filter and Dynamic Visibility Logic

### Filter Selected

```DAX
Filter_Selected = 
IF(
    OR(
        ISFILTERED('PROD  of the Day'[Department]),
        OR(
            ISFILTERED('PROD  of the Day'[Operator]),
            OR(
                ISFILTERED('PROD  of the Day'[Machine]),
                OR(
                    ISCROSSFILTERED('PROD  of the Day'[Date]),
                    HASONEVALUE('PROD  of the Day'[Date])
                )
            )
        )
    ),
    1,
    0
)
```

This measure controls whether selected KPI cards and metrics become visible when relevant filters are applied.

---

## 12. Time Calculations

### Total Time

```DAX
Total_time = 
[total_mr_hrs] + [tot_prod_hrs] + [NonProductive_Hrs]
```

---

## 13. Previous Day Analysis

### Previous Day OEE

```DAX
PREVIOUS_DAY_OEE = 
CALCULATE(
    [OEE %],
    DATEADD(
        'PROD  of the Day'[Date],
        -1,
        DAY
    )
)
```

---

## 14. Machine Rated Speed Logic

```DAX
Rated_Speed_Per_Shift = 
VAR MachineName = TRIM('PROD  of the Day'[Machine])
RETURN
SWITCH(
    TRUE(),
    MachineName = "1113 PAPER CUTTING MACHINE HPM 115 (I)", 150000,
    MachineName = "1114 PAPER CUTTING MACHINE HPM 115 (II)", 150000,
    MachineName = "1115 HIGH SPEED SHEET CUTTER MACHINE - HSC 1400D", 150000,
    MachineName = "1202 KOMORI 640 + CX UV", 144000,
    MachineName = "1205 KOMORI L-240", 120000,
    MachineName = "1207 KOMORI GL 640", 196800,
    MachineName = "1208 KOMORI GL 637", 180000,
    MachineName = "1209 KOMORI GL 637 IR+UV", 180000,
    MachineName = "1301 HEIDELBERG SM 102 E+L", 45000,
    MachineName = "1401 PS GRAPHICS LAMINATION 900", 20000,
    MachineName = "1403 PS GRAPHICS LAMINATION AUTOMATIC", 10000,
    MachineName = "1406 ROLL TO ROLL FILM LAMINATION", 50000,
    MachineName = "1407 HIGH SPEED AUTOMATIC DRY LAMINATION GS-R 110", 50000,
    MachineName = "1516 AUTOPRINT CHECKMATE 50", 400000,
    MachineName = "1605 MANUAL PUNCHING – ASSOCIATED – 20X26", 8000,
    MachineName = "1606 MANUAL PUNCHING – FRIENDS – 25X37", 8000,
    MachineName = "1607 MANUAL PUNCHING – CENTURY – 22X32", 8000,
    MachineName = "1608 MANUAL PUNCHING – ASSOCIATED – 20X26", 8000,
    MachineName = "1609 MANUAL PUNCHING – ASSOCIATED – 25X37", 8000,
    MachineName = "1611 MANUAL PUNCHING RAVI 32X42", 8000,
    MachineName = "1612 MANUAL PUNCHING - - SUJATA – 32X42", 8000,
    MachineName = "1616 WENHONG 1050 SS", 40000,
    MachineName = "1617 GUANGYA LK 800 M", 40000,
    MachineName = "1618 GUANGYA LK 800 M", 50000,
    MachineName = "1619 BRAUSSE - 1050 I", 40000,
    MachineName = "1620 AUTOMATIC DIE PUNCHING & FOIL STAMPING ( WENHONG 1050SF)", 40000,
    MachineName = "1621 AUTOMATIC DIE PUNCHING & STRIPPING (WENHONG 1080 SS)", 30000,
    MachineName = "1701 H & S WP SPEEDLINER", 150000,
    MachineName = "1702 KOHMANN - F-1000", 50000,
    MachineName = "1705 WENHONG WINDOW PATCHING", 60000,
    MachineName = "1802 PAKTEK GM 550", 250000,
    MachineName = "1805 FOSHAN DOUBLE SIDE OUTER PASTING", 40000,
    MachineName = "1807 BOBST AMBITION", 400000,
    MachineName = "1808 DOUBLE SIDE SEMI AUTO COMBINED GLUER", 10000,
    MachineName = "1809 DGM TECHNOFOLD 1100 SL", 150000,
    MachineName = "1811 WENHONG 1100", 150000,
    MachineName = "1812 WENHONG 650", 250000,
    MachineName = "1813 ROBUS AUTOMATIC FOLDER GLUER MACHINE FG-1100", 200000,
    MachineName = "2202 CREOSCREEN-40", 20000,
    MachineName = "2301 XINGUANG B&F CORRUGATION", 100000,
    MachineName = "2303 IPACK CANGZHOU B & A FLUTE CORRUGATION", 125000,
    MachineName = "1405 YONGSHUN AUTO LAMINATION", 50000,
    MachineName = "1621 AUTOMATIC DIE PUNCHING & STRIPPING (WENHONG 1180 SS)", 30000,
    MachineName = "1622 WENHONG 1050SS-25", 50000,
    MachineName = "2201 SCREEN PRINTING", 50000,
    MachineName = "2302 XINGUANG B FLUTE CORRUGATION", 150000,
    MachineName = "2408 WENHONG 3 PLY FLUTE LAMINATOR", 50000,
    MachineName = "2409 LAMIFY 5 PLY FLUTE LAMINATOR", 30000,
    MachineName = "2410 AMPLE 3 PLY FLUTE LAMINATOR", 50000,
    MachineName = "2411 AMPLE HW-1450 HIGH SPEED FLUTE LAMINATOR", 50000,
    MachineName = "1704 H & S WP SPEEDLINER", 150000,
    MachineName = "1109 HIGH SPEED SHEET CUTTER", 150000,
    BLANK()
)
```

---

## 15. Measure Summary

| Area | Measures |
|---|---|
| OEE | OEE %, OEE_loss, CURRENT_OEE, OEE_Visible |
| Availability | Availability %, availability_loss, Availability_Visible, Actual_Run_Time, Planned_Time |
| Performance | Performance %, performance_loss, Performance_Visible, Planned_Production_Qty |
| Quality | Quality %, quality_loss, Quality_Visible |
| Production | Good_Qty, Total_prod_qty, Wastage_Qty, act_pro_qty, tot_prod_hrs |
| MR / Make Ready | total_mr_hrs, Avg_per_MR, Avg_MR_per_Shift, Avg_MR_Time_Per_Row_Minutes |
| Non-Productive | NonProductive_Hrs, Non_PRODUCTIVE_hrs_Visible |
| Shifts | Total_Available_Shifts, _Total_Available_Shifts, Dynamic_Available_Shifts |
| Visibility | Filter_Selected and multiple *_Visible measures |
| Machine Logic | Rated_Speed_Per_Shift |
| Comparison | PREVIOUS_DAY_OEE |
| Production Rate | Avg_Production_Per_Hour, Production_Per_Shift |

---

## Notes

- The primary source table used by these calculations is `PROD  of the Day`.
- Availability is based on a 12-hour available time per machine/shift.
- Normal days use two shifts, while Sunday uses one shift.
- The holiday-aware shift calculation includes the configured holiday dates.
- Machine-specific rated production speeds are defined through `Rated_Speed_Per_Shift`.
- Visibility measures are used to dynamically control KPI display based on dashboard filter selection.

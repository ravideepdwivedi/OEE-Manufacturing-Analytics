SELECT  
    pr.shift AS shift,
    jo.operation AS operation,
    m.machine_name AS machine_name,
    sp.date AS date,
    sp.other_name AS jdf_name,
    sp.production AS production_qty,
    sp.wastage AS wastage_qty,
    sp.mr_hrs AS mr_hrs,
    sp.prod_hrs AS prod_hrs,
    sp.operator_name AS operator_name
FROM `mannaterp-2019`.shift_production sp  

JOIN `mannaterp-2019`.order_booking ob 
    ON ob.order_id = sp.job_name

JOIN `mannaterp-2019`.erp_machine m 
    ON m.machine_id = sp.mch_id

LEFT JOIN `mannaterp-2019`.production_report pr
    ON pr.report_id = sp.report_id

LEFT JOIN (
        SELECT 
            report_id,
            shiftids,
            MAX(operation) AS operation
        FROM `mannaterp-2019`.job_operations
        GROUP BY report_id, shiftids
) jo
    ON jo.report_id = sp.report_id
    AND FIND_IN_SET(sp.shift_id, jo.shiftids)

WHERE sp.date > '2025-10-11'

ORDER BY sp.date DESC;

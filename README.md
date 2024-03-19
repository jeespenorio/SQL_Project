# SQL_Project
Creating Up to Manipulation of Data
-- Table: public.2022_AC

-- DROP TABLE IF EXISTS public."2022_AC";

CREATE TABLE IF NOT EXISTS public."AC_2022"
(
    make character varying COLLATE pg_catalog."default",
    model character varying COLLATE pg_catalog."default",
    yeara character varying COLLATE pg_catalog."default",
    yearb character varying COLLATE pg_catalog."default",
    fuel_system character varying COLLATE pg_catalog."default",
    cc character varying COLLATE pg_catalog."default",
    cylinder_number character varying COLLATE pg_catalog."default",
    power_reed character varying COLLATE pg_catalog."default",
    rage_cage character varying COLLATE pg_catalog."default",
    ragecage_replacement_reed character varying COLLATE pg_catalog."default",
    ragecage_replacement_gasket character varying COLLATE pg_catalog."default",
    ragecage_replacement_boot character varying COLLATE pg_catalog."default",
    ragecage_replacement_clamp character varying COLLATE pg_catalog."default",
    ragecage_replacement_boot_clamp_kit character varying COLLATE pg_catalog."default",
    ssf character varying COLLATE pg_catalog."default",
    ssf_turbo character varying COLLATE pg_catalog."default",
    ct_lowtension character varying COLLATE pg_catalog."default",
    ct_midtension character varying COLLATE pg_catalog."default",
    ct_hightension character varying COLLATE pg_catalog."default",
    boyesenv_force_num character varying COLLATE pg_catalog."default",
    oemreed_valve_assembly_num character varying COLLATE pg_catalog."default",
    oem_manifold_intake_num character varying COLLATE pg_catalog."default"
)

TABLESPACE pg_default;

ALTER TABLE IF EXISTS public."2022_AC"
    OWNER to postgres;
	
----begin
SELECT *
FROM public."AC_2022";

--renaming tables
alter table public."AC_2022" rename yeara to year_start;
alter table public."AC_2022" rename yearb to year_end;

SELECT MAKE, MODEL, Year_start, Year_End
FROM public."AC_2022";

/*updates yeara*/

UPDATE public."AC_2022"
SET year_start = CASE
                WHEN year_start::integer < 30 THEN year_start::integer + 2000
                ELSE year_start::integer + 1900
            END;

/*updates yearb*/
UPDATE public."AC_2022"
SET year_end = CASE
                WHEN year_end::integer < 30 THEN year_end::integer + 2000
                ELSE year_end::integer + 1900
            END;


/*INDEX MATCH*/
SELECT MODEL, POWER_REED, Year_start, Year_end
FROM PUBLIC."AC_2022";

SELECT *
FROM AD_LIST;

/*Getting Matched_MPN in ADLIST*/


--cross join--
select a.make,a.model, a.power_reed ,b.* from public."AC_2022" a ,ad_list b;

--or using this join
--limit to 50 only

SELECT a.make, a.model, a.power_reed, b."MPN#", b."AD Item"
FROM public."AC_2022" a
CROSS JOIN ad_list b
limit 50;

-- for power_reed
SELECT a.make, a.model, a.year_start, a.year_end, a.power_reed, b."MPN#", b."AD Item", b."VENDOR"
FROM public."AC_2022" a
LEFT JOIN ad_list b ON a.power_reed = b."MPN#"
LIMIT 150;

--for rage_cage

SELECT a.make, a. year_start, a.year_end, a.model, a.rage_cage, b."MPN#", b."AD Item"
FROM public."AC_2022" a
LEFT JOIN ad_list b ON a.rage_cage = b."MPN#"
LIMIT 150;

--for ragecage_replacement_reed

SELECT a.make, a.model, a. year_start, a.year_end, a.ragecage_replacement_reed, b."MPN#", b."AD Item"
FROM public."AC_2022" a
LEFT JOIN ad_list b ON a.ragecage_replacement_reed = b."MPN#"
LIMIT 150;

-- for ragecage_replacement_gasket

SELECT a.make, a.model, a. year_start, a.year_end, a.ragecage_replacement_gasket, b."MPN#", b."AD Item"
FROM public."AC_2022" a
LEFT JOIN ad_list b ON a.ragecage_replacement_gasket = b."MPN#"
LIMIT 150;

--for ragecage_replacement_boot

SELECT a.make, a.model, a. year_start, a.year_end, a.ragecage_replacement_boot, b."MPN#", b."AD Item"
FROM public."AC_2022" a
LEFT JOIN ad_list b ON a.ragecage_replacement_boot = b."MPN#"
LIMIT 150;

--for ragecage_replacement_clamp

SELECT a.make, a.model, a. year_start, a.year_end, a.ragecage_replacement_clamp, b."MPN#", b."AD Item"
FROM public."AC_2022" a
LEFT JOIN ad_list b ON a.ragecage_replacement_clamp = b."MPN#"
LIMIT 150;

--for ragecage_replacement_boot_clamp_kit
SELECT a.make, a.model, a. year_start, a.year_end, a.ragecage_replacement_boot_clamp_kit, b."MPN#", b."AD Item"
FROM public."AC_2022" a
LEFT JOIN ad_list b ON a.ragecage_replacement_boot_clamp_kit = b."MPN#"
LIMIT 150;

--for ssf
SELECT a.make, a.model, a. year_start, a.year_end, a.ssf, b."MPN#", b."AD Item"
FROM public."AC_2022" a
LEFT JOIN ad_list b ON a.ssf = b."MPN#"
LIMIT 150;

--for ssf_turbo
SELECT a.make, a.model, a.ssf_turbo, b."MPN#", b."AD Item"
FROM public."AC_2022" a
LEFT JOIN ad_list b ON a.ssf_turbo = b."MPN#"
LIMIT 150;

--for ct_lowtension
SELECT a.make, a.model, a. year_start, a.year_end, a.ct_lowtension, b."MPN#", b."AD Item"
FROM public."AC_2022" a
LEFT JOIN ad_list b ON a.ct_lowtension = b."MPN#"
LIMIT 150;

--for ct_midtension
SELECT a.make, a.model, a. year_start, a.year_end, a.ct_midtension, b."MPN#", b."AD Item"
FROM public."AC_2022" a
LEFT JOIN ad_list b ON a.ct_midtension = b."MPN#"
LIMIT 150;

--for ct_hightension
SELECT a.make, a.model, a. year_start, a.year_end, a.ct_hightension, b."MPN#", b."AD Item"
FROM public."AC_2022" a
LEFT JOIN ad_list b ON a.ct_hightension = b."MPN#"
LIMIT 150;

--for boyesenv_force_num
SELECT a.make, a.model, a. year_start, a.year_end, a.boyesenv_force_num, b."MPN#", b."AD Item"
FROM public."AC_2022" a
LEFT JOIN ad_list b ON a.boyesenv_force_num = b."MPN#"
LIMIT 150;

--for oemreed_valve_assembly_num
SELECT a.make, a.model, a. year_start, a.year_end, a.oemreed_valve_assembly_num, b."MPN#", b."AD Item"
FROM public."AC_2022" a
LEFT JOIN ad_list b ON a.oemreed_valve_assembly_num = b."MPN#"
LIMIT 150;

--for oem_manifold_intake_num
SELECT a.make, a.model, a. year_start, a.year_end, a.oem_manifold_intake_num, b."MPN#", b."AD Item"
FROM public."AC_2022" a
LEFT JOIN ad_list b ON a.oem_manifold_intake_num = b."MPN#"
LIMIT 150;

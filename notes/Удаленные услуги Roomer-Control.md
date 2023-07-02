```sql
SELECT --count(*)--, -- 7794 шт.
roomer_issues.id AS "roomer.id",
roomer_issues.status AS "roomer.status",
roomer_issues.scontrol_id,
to_char(roomer_issues.created, 'DD.MM.YYYY HH24:MI:SS'::text) AS "roomer.created"
FROM dblink('
host=10.20.28.77
port=30116
connect_timeout=10
dbname=sroomer
user=dblink_user
password=Cnhjqrf2023
'::text, 'SELECT
id,
status,
scontrol_id,
created
FROM
issues_issue
ORDER BY created DESC'::text) roomer_issues(id integer, status text, scontrol_id integer, created timestamp without time zone)
where
--roomer_issues.id = '127415' and
roomer_issues.scontrol_id not in (select id from issues_issue where kind = 'app')
and roomer_issues.scontrol_id not in (select id from issues_issueservice)
and roomer_issues.scontrol_id in (select distinct id from issues_historicalissueservice)
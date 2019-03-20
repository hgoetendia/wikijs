<!-- TITLE: Edit/List function -->


It will open the source code of the function in editable format. You will not only be able to view it, you can edit and execute it as well.

# Edit function

```pgsql
\ef <function_name>
```

# List function


```pgsql
$ pg_dump -Fc -s | pg_restore -l | grep fn_myfunc
5528; 1255 17096 FUNCTION accounting fn_myfunc(character varying, character varying) postgres
```

Then

```pgsql
$ pg_dump -Fc -s | pg_restore -P 'fn_myfunc(character varying, character varying)'
--
-- PostgreSQL database dump
--

-- Dumped from database version 9.5.6
-- Dumped by pg_dump version 9.5.6

SET statement_timeout = 0;
SET lock_timeout = 0;
SET client_encoding = 'UTF8';
SET standard_conforming_strings = on;
SET check_function_bodies = false;
SET client_min_messages = warning;
SET row_security = off;

SET search_path = config, pg_catalog;

--
-- Name: fn_myfunc(character varying, character varying); Type: FUNCTION; Schema: public; Owner: postgres
--

CREATE FUNCTION fn_myfunc(p character varying, p_tag character varying) RETURNS TABLE(id integer, foo character varying, test character varying, id2 integer, description character varying, status character varying)
    LANGUAGE plpgsql
    AS $$

DECLARE
BEGIN

RETURN QUERY
SELECT *
FROM   footable
WHERE  1=1
AND    2=2;

END;
$$;


ALTER FUNCTION public.fn_myfunc(p character varying, p_tag character varying) OWNER TO postgres;

--
-- PostgreSQL database dump complete
--


```




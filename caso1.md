# base_datos_c3_q2
Se requiere crear una consulta para:
    Obtener de manera ordenada la lista de vistas y modulos a los que tiene acceso un rol en estado activo. 
    role[name=> rol, route => ruta]
    module[name=> modulo, route => paquete]

    Nota: order by atributo
    SELECT 
        * 
    FROM 
        persona p
    ORDER BY p.nombre

```sql
SELECT 
    r.name AS rol,
    m.name AS nombre,
    m.path AS paquete,
    v.name AS vista,
    v.path AS ruta
FROM
    role r 
    INNER JOIN role_module rm ON r.id = rm.role_id
    INNER JOIN module m ON rm.module_id = m.id
    INNER JOIN module_view mv ON m.id = mv.module_id
    INNER JOIN view v ON mv.view_id = v.id 
WHERE r.state = true
ORDER BY r.name
```

# Resultado

![Consulta completa](img/IMG_1.png)
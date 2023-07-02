Apdex - это метрика, которая используется для измерения уровня удовлетворенности пользователей при работе с приложением. Для расчета Apdex используется следующая формула:

Apdex = (satisfying + tolerating/2) / total

Где:
- satisfying - количество пользователей, которые быстро получили ответ от приложения (обычно это время ответа до 2 секунд);
- tolerating - количество пользователей, которые получили ответ от приложения с задержкой (обычно это время от 2 секунд до 4 секунд);
- total - общее количество пользователей, которые использовали приложение.

Важно отметить, что максимальное значение Apdex равно 1, а минимальное - 0. Чем ближе значение Apdex к 1, тем более качественно работает приложение и выше уровень удовлетворенности пользователей

> [!Формула в Grafana]
> (sum(rate(nginx_ingress_controller_request_duration_seconds_bucket{ingress!="",ingress=~"$pods.*", le="0.1", code!="5.."}[10m])) by (ingress) + (sum(rate(nginx_ingress_controller_request_duration_seconds_bucket{ingress!="",ingress=~"$pods.*", le="0.5", code!="5.."}[10m])) by (ingress) - sum(rate(nginx_ingress_controller_request_duration_seconds_bucket{ingress!="",ingress=~"$pods.*", le="0.1", code!="5.."}[10m])) by (ingress)) / 2) / sum(rate(nginx_ingress_controller_request_duration_seconds_bucket{ingress!="",ingress=~"$pods.*", le="+Inf"}[10m])) by (ingress) * 100



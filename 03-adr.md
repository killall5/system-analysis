# ADR-001: Выделение сервиса "Матчинг воркеров" в качестве отдельного сервиса системы Make cats free again

## Status: Proposed

## Context

Основываясь на консерне топ-менеджеров компании, было определено, что сервис "Матчинг воркеров" должен иметь релизный цикл не реже, чем 1 раз в неделю.

Также, в отделе занимающимся разработкой алгоритмов, образовался специфический язык "эталонный образец" и "обычный образец", именуемые в остальных частях системы "клиент" и "воркер", соответственно (требование US-290).

Также консерн топ-менеджеров заключается в том, чтобы данную функциональность можно было продавать и дорабатывать отдельно от остальной системы.

Сервис должен обладать характеристиками:

- **modifiability** и **maintainability**, а значит **testability** и **deployability** напрямую вытекающие из консерна топ-менеджмента "Благодаря отсеву и матчингу компания планирует выделяться на фоне конкурентов"
- релизный цикл не реже чем 1 раз в неделю. 


## Decision

Решение: выделить данный контекст в отдельный сервис. В силу требований USR-300, накладываемых на сервис, он должен быть реализован по архитектурному принципу Pipeline.

Также должно быть настроен автоматизированное тестирование каждого изменения, с покрытием тестами не ниже 90%.

Автоматизации также должно быть подвержено внедрение на стенд, с блокированием релиза если хотя бы один тест завершился ошибкой.


## Сompliance

Проверка будет осуществляться регулярно на основании прохождения тестов и уровня покрытия тестов.

Соблюдение архитектурного стиля автоматизировать невозможно, поэтому планируются периодическая проверка кода на соответствие документации.

## Alternatives

Сервис может использовать собственную БД, если это позволит улучшить показатели матчинга.
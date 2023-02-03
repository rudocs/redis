Цикл выпуска Redis

Как выпускаются новые версии Redis?

---

Redis — это системное программное обеспечение и тип системного программного обеспечения, в котором хранятся пользовательские данные, поэтому
он является одним из наиболее важных элементов программного стека.

По этой причине цикл выпуска Redis таков, что он обеспечивает высокостабильные
выпуски даже за счет более медленных циклов.

Новые выпуски публикуются в [репозитории Redis на GitHub](http://github.com/redis/redis),
а также доступны для [скачивания](/download). Объявления отправляются в
[список рассылки Redis](http://groups.google.com/group/redis-db) и
[@redisfeed в Twitter](https://twitter.com/redisfeed).

## Цикл выпуска

Данная версия Redis может иметь три разных уровня стабильности:

* Нестабильная(Unstable)
* Кандидат на выпуск(Release Candidate)
* Стабильная(Stable)

### Нестабильное дерево

Нестабильная версия Redis находится в `нестабильной` ветке
[репозитория Redis на GitHub](http://github.com/redis/redis).

Эта ветка является исходным деревом, в котором разрабатывается большинство новых функций.
`Нестабильная` версия не считается готовой к выпуску: она может содержать
критические ошибки, неполные функции и потенциально нестабильна.

Тем не менее, мы очень стараемся, чтобы даже нестабильная ветка могла использоваться большую часть
времени в среде разработки без существенных проблем.

### Кандидат на выпуск

Новые минорные и мажорные версии Redis начинаются как ответвления `нестабильной` ветки.
Название разветвленной ветки является плановым релизом.

Например, когда Redis 6.0 был выпущен в качестве кандидата на выпуск, `нестабильная`
ветка была разветвлена на ветку `6.0`. Новая ветка является
кандидатом на выпуск для этой версии.

Исправления ошибок и новые функции, которые могут быть стабилизированы в течение срока выпуска,
фиксируются в нестабильной ветке и переносятся в ветку
кандидат на выпуск. `Нестабильная` ветка может включать в себя дополнительную работу, которая не
является частью кандидата на выпуск и запланирована для будущих выпусков.

Первый релиз-кандидат, или RC1, выпускается после того, как его можно будет использовать в
целях разработки и для тестирования новой версии. На данном этапе большинство
новых функций и изменений, внесенных в новую версию, готовы к рассмотрению,
а цель выпуска собрать отзывы общественности.

Последующие кандидаты на выпуск выходят каждые три недели или около того, в основном
для исправления ошибок. Они также могут добавлять новые функции и вносить изменения, но с
меньшей скоростью и меньшим потенциальным риском для окончательного кандидата на
выпуск.

### Стабильное дерево

Как только разработка завершена и частота отчетов о критических ошибках для кандидата на выпуск 
уменьшается, он готов к окончательному выпуску. На этом этапе
выпуск помечается как стабильный и выпускается с номером "0" в качестве версии уровня
патч.

## Версионирование

Стабильные выпуски свободно следуют обычной семантической схеме управления версиями
`major.minor.patch`. Основная цель — предоставить явные гарантии
обратной совместимости.

### Патч версии(Patch)

Патчи в основном состоят из исправлений ошибок и очень редко вызывают какие-либо
проблемы совместимости.

Обновление с предыдущей версии уровня патч почти всегда безопасно и
без проблем.

Могут быть добавлены новые функции и директивы конфигурации или изменены
значения по умолчанию, если они не оказывают существенного влияния или не создают проблем,
связанных с эксплуатацией.

### Минорные версии(Minor)

Минорные версии обычно обеспечивают зрелость и расширенную функциональность.

Обновление между минорными версиями не приводит к проблемам совместимости
на уровне приложений.

Минорные выпуски могут включать новые команды и типы данных, которые вносят несовместимость,
связанную с операциями, включая изменения в формате сохраняемости данных
и протоколе репликации.

### Мажорные версии(Major)

В мажорных версиях представлены новые возможности и значительные изменения.

В идеале они не создают проблем совместимости на уровне приложений.

## График выпуска

Выпуск новой мажорной версии планируется раз в год.

Как правило, за каждым мажорным выпуском через шесть месяцев следует минорная версия.

Патчи выпускаются по мере необходимости для устранения неотложных проблем или после того, как стабильная
версия накопит достаточно исправлений, чтобы оправдать это.

Для связи с основной командой по деликатным вопросам и вопросам безопасности, пожалуйста,
напишите по электронной почте [redis@redis.io](mailto:redis@redis.io).

## Поддержка

Как правило, более старые версии не поддерживаются, так как мы очень стараемся сделать
API Redis в основном обратно совместимым.

Обновление до более новых версий является рекомендуемым подходом и обычно является тривиальным.

Последняя стабильная версия всегда полностью поддерживается и обслуживается.

Две дополнительные версии получают только техническое обслуживание, что означает, что только исправления
критических ошибок и больших проблем безопасности фиксируются и выпускаются в виде патчей:

* Предыдущая минорная версия из последней стабильной версии.
* Предыдущий стабильный мажорный выпуск.

Например, рассмотрим следующие гипотетические версии: 1.2, 2.0, 2.2, 3.0,
3.2.

Когда версия 2.2 является последним стабильным выпуском, поддерживаются как 2.0, так и 1.2.

Как только версия 3.0.0 заменит 2.2 в качестве последней стабильной версии, версии 2.0 и 2.2 будут
поддерживаться, а версия 1.x подойдет к концу.

Этот процесс повторяется с версией 3.2.0, после чего поддерживаются только версии 2.2 и 3.0.

Вышеизложенное является рекомендациями, а не установленными правилами, и они не заменят
здравый смысл.
# Предварительная подготовка
- Шаблон предназначен для использования на [GitHub Pages](https://pages.github.com). Это означает, что вам нужно загрузить проект в репозиторий и произвести необходимые настройки, чтобы сайт заработал.
- За основу взят [этот](https://github.com/maximevaillancourt/digital-garden-jekyll-template) проект.
- Для того, чтобы все работало, под сайт нужен домен, либо репозиторий, в который загружается проект должен иметь название аккаунта («username.github.io»)
- В настройках репозитория, в пункте «Pages», в пункте «Build and deployment», в качестве build source вам нужно выбрать «Github Actions»

# Настройка проекта Obsidian
- Вам нужно открыть папку `_notes` как Obsidian проект.
- Папка «Шаблоны» игнорируется при сборке проекта. Вы можете переименовать ее – в этом случае вам также нужно изменить строку `exclude: ` в файле «`_config.yml`».
- Все заметки должны иметь метаданные:
	- date – дата, которая будет указана как дата публикации заметки. Можно убрать или изменить, переписав код.
	- slug – адрес заметки, по которой она будет доступна в интернете. Тут должно быть указано только имя самой страницы, адрес сайта подставится автоматически
	- tag – массив тэгов. По задумке, страница не может иметь несколько категорий, но вы можете использовать в качестве дополнительной категории «избранное» – тэг «signum». Несколько тэгов указываются через запятую: `tag: [fabula, signum]`
	- priority – числовое значение, «вес» замекти, по которой она будет сортироваться в определенных случаях

# Настройка структуры сайта
Сайт имеет следующую структуру:
- `_config.yml` – это файл настроек сайта. Вам нужно вставить адрес вашего сайта в 13 строчку в поле «url».
- `_pages/index.md` – главная страница. Тут поиск и ссылки на проекты и их категории. Поиск срабатывает при начале ввода с клавиатуры, либо при клике в поле.
- `_projects/` – папка страниц проекта. Назначение проекта (страница `project1.md`) – большая категория, включающая в себя под-категории (тэги). Вам нужно изменить название файла и содержимое метаданных:
	- title – название проекта
	- slug – адрес, по которому будет открываться страница проекта
	- intags и intags2 – вам нужно заполнить тэги, которые относятся к проекту. Эти поля идентичны – строка со значениями через запятую, только в поле intags нужны квадратные скобки (особенности кода).
	- description – описание проекта.
- `_tagpages/` – папка с тэгами. Каждый тэг (страница `notas.md`) – это подкатегория внутри проекта. Для каждого тэга нужно заполнить метаданные:
	- description – описание тэга
	- slug – адрес страницы тэга
	- title – название в единтсвенном числе. Например: «Заметка»
	- titles – название в множественном числе. Например: «Заметки»
- `_tagpagesearches/` – папка с настройками для поиска заметок по тегам. Каждый `.json` файл должен быть синхронизирован с `.md` файлом в папке `_tagpages/`. Файл должен иметь название тэга, а в содержимом файла должна быть изменена строка 3 и 7 – туда должно быть подставлено название тэга.

# Дополнительные настройки сайта
- Следующие страницы могут быть вам полезны:
	- `_pages/chronology.md` – хронология добавления заметок
	- `_pages/updates.md` – схожая по смыслу, но немного отличная по дизайну страница
	- `_pages/search.md` – страница, посвященная поиску. Раньше он был вынесен отдельно, сейчас размещен на главной странице для упрощения доступа.
	- `404.html` – страница ошибки, которая выводится в случае, если адреса запрашиваемой страницы не существует.
- `assets/favicon.png` – иконка сайта, вам нужно заменить ее на свою.
- Стили сайта размещены в `assets/style.css`
- По умолчанию включено расширение `backlinks_light_grouped_light.html`, генерирующее обратные ссылки, группирующее их по тэгам и расставляющее исходящие и входящие ссылки к каждой страницы. Все расширения обратных ссылок находятся в папке `_includes/`. Их можно включить в шаблоне `_layouts/note.html`, заменив в 25 строке название файла-расширения после слова `include`.
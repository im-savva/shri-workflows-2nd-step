# Конфиги

## Конфиг Prettier

| Параметр            | Значение | Описание                                                                                                                                                |
| ------------------- | -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **bracketSameLine** | false    | В tsx закрывающая скобка ставится на следующей строке                                                                                                   |
| **bracketSpacing**  | true    | Для объектов пробелы внутри скобок не добавляются (соответствует CodeStyle)                                                                             |
| **endOfLine**       | "lf"     | Использует LF для переводов строк (соответствует CodeStyle)                                                                                             |
| **singleQuote**     | true     | Используются одинарные кавычки для различия js/ts и html/jsx/tsx                                                                                        |
| **tabWidth**        | 2        | Отступ 2 пробела (вместо 4) для увеличения полезной информации на экране                                                                                |
| **printWidth**      | 120      | Максимальная длина строки — 120. Соответствует CodeStyle                                                                                                |

Для **bracketSameLine** пример
с переносом:

```tsx
<Typo element={TypoElement.div} view={TypoView.h7} className={s.blocks__list}>
  <RichText content={text} />
</Typo>
```

без переноса:

```tsx
<Typo element={TypoElement.div} view={TypoView.h7} className={s.blocks__list}>
  <RichText content={text} />
</Typo>
```

## Конфиг Eslint

Изначально необходимо выбрать используемые плагины

```js
plugins: ["@typescript-eslint", "import", "prettier", "react", "react-hooks"];
```

И применяем правила из этих плагинов:

```js
extends: [
  'eslint:recommended', // основные правила eslint
  'plugin:@typescript-eslint/recommended', // правила для TypeScript
  'plugin:react/recommended', // правила для реакта
  'plugin:react/jsx-runtime', // правила для jsx
  'plugin:react-hooks/recommended', // правила для хуков
  'plugin:import/warnings', // все для проверки импортов (следующие 2 тоже)
  'plugin:import/errors',
  'plugin:import/typescript',
  'plugin:prettier/recommended', // для форматировщика
]
```

Далее надо записать правила:

```js
rules: {
  // Отключает проверку на количество строк в файле
  'max-lines': 'off',

  // Запрещает циклические импорты, разрешает глубину до 3 уровней
  'import/no-cycle': [
    'error',
    {
      maxDepth: 3,
    },
  ],

  // Включает проверку сложности кода с максимумом 10
  complexity: ['error', { max: 10 }],

  // Отключает проверку на неправильные пробелы (например, нулевые символы и т.д.)
  'no-irregular-whitespace': 'off',

  // Требует использовать фигурные скобки для всех блоков (if, else и т.д.)
  curly: ['error', 'all'],

  // Требует использовать одинарные кавычки (как и prettier)
  quotes: ['error', 'single'],

  // Запрещает использование alert
  'no-alert': 'error',

  // Предупреждает о console.log и других console вызовах
  'no-console': 'warn',

  // Запрещает повторное объявление переменных
  'no-redeclare': 'error',

  // Запрещает использование var
  'no-var': 'error',

  // Настройка порядка импортов
  'import/order': [
    'error',
    {
      groups: ['builtin', 'external', 'internal', 'parent', 'sibling', 'index'],
      alphabetize: {
        order: 'asc',
      },
      'newlines-between': 'always',
      pathGroups: [
        {
          pattern: '*/**/*.scss',
          group: 'sibling',
          position: 'after',
        },
        {
          pattern: './*.scss',
          group: 'sibling',
          position: 'after',
        },
      ],
    },
  ],

  // Отключает правило про импорт по умолчанию
  'import/default': 'off',

  // Отключает правило, запрещающее экспортировать default, если имя совпадает
  'import/no-named-as-default': 'off',

  // Запрещает использовать шаблонные строки как обычные строки
  'no-template-curly-in-string': 'error',

  // Отключает принудительное деструктурирование
  'prefer-destructuring': 'off',

  // Требует использование const вместо let, если переменная не переопределяется
  'prefer-const': 'error',

  // Требует использовать стрелочные функции вместо обычных function в коллбеках
  'prefer-arrow-callback': 'error',

  // Интеграция с Prettier — ошибки форматирования считаются ошибками ESLint
  'prettier/prettier': 'error',

  // Требует импортировать React переменные, используемые в JSX
  'react/jsx-uses-react': 'error',

  // Требует использовать переменные, которые содержат JSX (чтобы избежать false positive)
  'react/jsx-uses-vars': 'error',

  // Предпочитает функциональные компоненты, если не требуется состояние
  'react/prefer-stateless-function': 'error',

  // Требует точку с запятой
  semi: 'error',

  // Отключает правило, запрещающее использование any
  '@typescript-eslint/no-explicit-any': 'off',

  // Отключает правило про префиксы у интерфейсов (например, IExample)
  '@typescript-eslint/interface-name-prefix': 'off',

  // Запрещает неиспользуемые переменные
  '@typescript-eslint/no-unused-vars': 'error',

  // Отключает правило про camelCase (например, разрешает snake_case)
  '@typescript-eslint/camelcase': 'off',

  // Отключает запрет на require
  '@typescript-eslint/no-var-requires': 'off',

  // Отключает запрет на использование `@ts-` комментариев
  '@typescript-eslint/ban-ts-comment': 'off',

  // Отключает проверку на управляющие символы в регулярках
  'no-control-regex': 'off',

  // Обязывает вставлять пустую строку между определёнными конструкциями
  'padding-line-between-statements': [
    'error',
    {
      // Пустая строка перед return, block-like, throw, if, function, default
      blankLine: 'always',
      prev: '*',
      next: ['return', 'block-like', 'throw', 'if', 'function', 'default'],
    },
    {
      // Пустая строка после block-like, throw, if, function
      blankLine: 'always',
      prev: ['block-like', 'throw', 'if', 'function'],
      next: '*',
    },
  ],
  
  // Запрещает магические числа (числа без объяснения)
  'no-magic-numbers': ['warn', { ignore: [-1, 0, 1, 2] }],
  
  // Запрещает дублирование кода в условиях
  'no-dupe-else-if': 'error',
  
  // Требует использования === вместо ==
  eqeqeq: 'error',
  
  // Запрещает пустые блоки кода
  'no-empty': 'error',
  
  // Запрещает fallthrough в switch без комментария
  'no-fallthrough': 'error',
  
  // Запрещает переопределение встроенных объектов
  'no-global-assign': 'error',
}
```

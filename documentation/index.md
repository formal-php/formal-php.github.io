---
hide:
    - navigation
    - toc
---

# Welcome to Formal

!!! success ""
    Formal is all about data storages.

You'll find packages to:

- connect to them
- high abstractions to simplify storing
- tools to manage the lifecycle of storages

They use declarative code to provide a memory safe approach to data manipulation.

<div class="grid cards" markdown>

-   :material-connection: [`formal/access-layer`](https://formal-php.github.io/access-layer/)

    ---

    Use objects to progamatically build your queries instead of concatening strings.

    ```php
    $pdo = PDO::of(Url::of('mysql://user:pwd@127.0.0.1:3306/db'));

    $_ = $pdo(
        Select::from(
            Table\Name::of('users'),
        ),
    )
        ->map(User::fromRow(...))
        ->foreach(doSomething(...));
    ```

-   :material-database-outline: [`formal/orm`](https://formal-php.github.io/orm/)

    ---

    Manipulate your Domain objects and let the ORM store them (SQL, Elasticsearch or Filesystem).

    ```php
    $_ = $manager
        ->repository(User::class)
        ->matching(Property::of(
            'email',
            Sign::endsWith,
            '@your-company.com',
        ))
        ->foreach(
            sendResetPasswordEmail(...),
        );
    ```

-   :material-vector-difference: [`formal/migrations`](https://formal-php.github.io/migrations/)

    ---

    Incrementally run SQL queries to update your database. Or run commands when you deploy.

    ```php
    $dsn = Url::of('mysql://user:pwd@127.0.0.1:3306/db');

    $migrations
        ->storeVersionsInDatabase($dsn)
        ->sql()
        ->files(
            Path::of('migrations/folder/'),
        )
        ->migrate($dsn);
    ```

</div>


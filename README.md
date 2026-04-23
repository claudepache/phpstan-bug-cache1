A reproducer of a bug in PHPStan 2.1.51 (https://github.com/phpstan/phpstan/issues/14520)

Steps to reproduce:

1. Clone this repo.
2. `phpstan clear-result-cache`.
3. Run `phpstan`. There should be the following error on `test.php`, line 3: “Parameter #1 $x of class c constructor expects list<string>, array{null} given.”
4. Modify the file `c.php`, replacing `/** @var list<string> */` with `/** @var list<?string> */` on line 6.
5. Run `phpstan` again. The error incorrectly persists.
6. Clear the cache with `phpstan clear-result-cache` and run `phpstan` again. The error correctly disappears.

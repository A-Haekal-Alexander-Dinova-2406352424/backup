# Commit History Compliance (Tutorial 1 / `70-90.pdf`)

This document maps the **required commit checkpoints** in `70-90.pdf` (pages **69–89**) to the **actual commits and merge commits** in this repository.

## How to Verify (commands)

- View full graph: `git log --graph --decorate --oneline --all`
- Show files changed per commit: `git show --name-status <commit>`
- Prove a merge commit is explicit (2 parents): `git show -s --pretty=format:"%h parents:%p %s" <merge_commit>`

## Project Scaffold (PDF p.69–71)

PDF requirement: create Spring Boot project, create git repo, commit, push.

- Commit: `83ccb72` — `Add Spring Boot project scaffold`
  - Adds generated project files (Gradle wrapper, `build.gradle.kts`, `src/`, etc.).

## Feature Iteration 1 — `list-product` Branch (PDF p.72–76)

PDF requirement: create branch `list-product`, then commit each step.

### Model: `Product.java` (PDF p.72)
- Branch: `list-product`
- Commit: `e0a537e` — `Add Product model`
  - Adds: `src/main/java/id/ac/ui/cs/advprog/eshop/model/Product.java`

### Repository: `ProductRepository.java` (PDF p.73)
- Branch: `list-product`
- Commit: `eb5db30` — `Add Product repository`
  - Adds: `src/main/java/id/ac/ui/cs/advprog/eshop/repository/ProductRepository.java`

### Service: `ProductService.java` + `ProductServiceImpl.java` (PDF p.74)
- Branch: `list-product`
- Commit: `a391db0` — `Add Product service`
  - Adds: `src/main/java/id/ac/ui/cs/advprog/eshop/service/ProductService.java`
  - Adds: `src/main/java/id/ac/ui/cs/advprog/eshop/service/ProductServiceImpl.java`

### Controller: `ProductController.java` (PDF p.75)
- Branch: `list-product`
- Commit: `e24aa36` — `Add Product controller`
  - Adds: `src/main/java/id/ac/ui/cs/advprog/eshop/controller/ProductController.java`

### Templates: `createProduct.html` + `productList.html` (PDF p.76)
- Branch: `list-product`
- Commit: `a80d8d4` — `Add product templates`
  - Adds: `src/main/resources/templates/createProduct.html`
  - Adds: `src/main/resources/templates/productList.html`

### Merge `list-product` → `main` (PDF p.77)
- Explicit merge commit on `main`: `92de5ea` — `Merge pull request #1 from .../list-product`
  - Proof (2 parents): `92de5ea parents:83ccb72 a80d8d4 ...`
  - PR link: https://github.com/A-Haekal-Alexander-Dinova-2406352424/backup/pull/1

## Exercise 1 — Edit/Delete Features (PDF p.77)

PDF requirement: create branches `edit-product` and `delete-product`, commit, push, then merge to `main`.

### `edit-product` branch
- Commit: `4ca5cfe` — `Add edit product feature`
- Explicit merge commit on `main`: `127986f` — `Merge pull request #2 from .../edit-product`
  - Proof (2 parents): `127986f parents:92de5ea 4ca5cfe ...`
  - PR link: https://github.com/A-Haekal-Alexander-Dinova-2406352424/backup/pull/2

### `delete-product` branch
- Commit: `bc3dbcf` — `Add delete product feature`
- Explicit merge commit on `main`: `f4aea52` — `Merge pull request #3 from .../delete-product`
  - Proof (2 parents): `f4aea52 parents:127986f bc3dbcf ...`
  - PR link: https://github.com/A-Haekal-Alexander-Dinova-2406352424/backup/pull/3

## Testing Preparation on `main` (PDF p.78)

PDF requirement: update `build.gradle.kts` (versions + dependencies + `unitTest`/`functionalTest` tasks), commit, push.

- Commit: `15d7e3c` — `Add unit and functional test setup`
  - Modifies: `build.gradle.kts`
- Commit: `002ded7` — `Fix Gradle test task config`
  - Modifies: `build.gradle.kts`
  - Note: this extra commit fixes a Gradle Kotlin DSL typo so `unitTest`/`functionalTest` tasks run correctly.

## Unit Tests — `unit-test` Branch (PDF p.79–81 + Exercise 2 p.88)

PDF requirement: create branch `unit-test`, commit unit tests, then add tests for edit/delete, commit, push, merge.

### `ProductTest.java` (PDF p.79)
- Branch: `unit-test`
- Commit: `8fa60be` — `Add Product unit tests`
  - Adds: `src/test/java/id/ac/ui/cs/advprog/eshop/model/ProductTest.java`

### `ProductRepositoryTest.java` (PDF p.80–81)
- Branch: `unit-test`
- Commit: `c6f8e8f` — `Add ProductRepository unit tests`
  - Adds: `src/test/java/id/ac/ui/cs/advprog/eshop/repository/ProductRepositoryTest.java`

### Exercise 2: Edit/Delete unit tests (PDF p.88)
- Branch: `unit-test`
- Commit: `f47f4c8` — `Add edit and delete unit tests`
  - Modifies: `src/test/java/id/ac/ui/cs/advprog/eshop/repository/ProductRepositoryTest.java`

### Merge `unit-test` → `main`
- Explicit merge commit on `main`: `021bd40` — `Merge pull request #4 from .../unit-test`
  - Proof (2 parents): `021bd40 parents:002ded7 f47f4c8 ...`
  - PR link: https://github.com/A-Haekal-Alexander-Dinova-2406352424/backup/pull/4

## Functional Tests — `functional-test` Branch (PDF p.85–87 + Exercise 2 p.88)

PDF requirement: create branch `functional-test`, create `HomePageFunctionalTest`, commit; then create `CreateProductFunctionalTest`, commit, push, merge.

### `HomePageFunctionalTest.java` (PDF p.85–87)
- Branch: `functional-test`
- Commit: `a15228b` — `Add home page functional test`
  - Adds: `src/test/java/id/ac/ui/cs/advprog/eshop/functional/HomePageFunctionalTest.java`
  - Adds: `src/main/resources/static/index.html` (to satisfy title = `ADV Shop` and `<h3>Welcome</h3>` requirement)

### Exercise 2: `CreateProductFunctionalTest.java` (PDF p.88)
- Branch: `functional-test`
- Commit: `d54880a` — `Add create product functional test`
  - Adds: `src/test/java/id/ac/ui/cs/advprog/eshop/functional/CreateProductFunctionalTest.java`

### Merge `functional-test` → `main`
- Explicit merge commit on `main`: `f117016` — `Merge pull request #5 from .../functional-test`
  - Proof (2 parents): `f117016 parents:021bd40 d54880a ...`
  - PR link: https://github.com/A-Haekal-Alexander-Dinova-2406352424/backup/pull/5

## Reflections in `README.md` (PDF p.77 + p.89)

PDF requirement: write Reflection 1 and Reflection 2 in `README.md` on `main`.

- Commit: `c69dd81` — `Add tutorial reflections`
  - Modifies: `README.md`

## Notes / Deviations (Transparency)

- The PDF specifies required commits/checkpoints; this repo includes **additional fixes** needed to make the Gradle test tasks work (`002ded7`), and an earlier `Initial commit` (`78b769d`) before the scaffold commit.
- No history rewriting was performed (no force-push, no squash merges). All feature branches were merged into `main` via PRs using explicit merge commits.


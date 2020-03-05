# Update to Angular 9

https://www.youtube.com/watch?v=TcdhAxDWWxM&feature=youtu.be&utm_source=email-sendgrid&utm_term=13952972&utm_medium=833442&utm_content=educational&utm_campaign=2020-02-06

- `Ivy` => new rendering engine => an under the hood change => smaller bundles...ie., less code for users to download => faster

- running `ng serve` => runs ahead of time compilation (rather than just in time compilation) => can be some bugs =>

## New Options for error handling

- `Basic Mode`

- `Full Mode`

- `Strict Mode` => to enable => `tsconfig.app.json` => https://angular.io/guide/angular-compiler-options => can add:

  ```json
    "angularCompilerOptions": {
      "fullTemplateTypeCheck": true,
      "preserveWhitespaces": true,
                ...
    }
    ```

  - if add:

  ```json
   "strictTemplates": true
   ```// get more errors for troubleshooting/checking..avoid extra mistakes

## Minor Breaking Changes

https://update.angular.io/

- if using `@ViewChild` => have to add `static` option:

   ```js
   @ViewChild({static: true})
   ```

  - or if already had (in Angular 8):

  ```js
   @ViewChild({static: false})
   ```

  - remove `false`


  ```js
   @ViewChild()
   ```

`cd ./`

`ng update @angular/cli @angular/core`//error => Repository is not clean. Please commit or stash any changes before updating In Angular 8 => see  https://stackoverflow.com/questions/56773528/repository-is-not-clean-please-commit-or-stash-any-changes-before-updating-in-a

- try:

`ng update @angular/cli @angular/core --allow-dirty`

- `aside` => enabled anonymous usage data w/ http://angular.io/analytics

   - To disable: `ng analytics project off`

- If you depend on many Angular libraries you may consider `speeding up your build` by invoking the ngcc (Angular Compatibility Compiler) in an npm postinstall script => https://update.angular.io/#8.1:9.0 => add this to `package.json` => can run ngcc after each installation of node_modules by adding a postinstall

```json
"postinstall": "ngcc --properties es2015 browser module main --first-only --create-ivy-entry-points"
````//Breaks deploy to Heroku..actually, might not have been the case...if using Procfile, make sure there is no space in beginning of command...

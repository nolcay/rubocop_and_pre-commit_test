RuboCop
=======


----------


RuboCop is a gem which checks if your code obeys the Ruby Style Guide to make your code look better.

For example:

 + Use tabs with a two space indent.
 + Keep lines less than 80 characters.
 + Never leave whitespace at the end of a line.
 + End each file with a blank line.
 + Use empty lines between `def`s to make the code block readable.
 + Don't use `then` for multi-line `if/unless` statements.
 + Use one expression per branch in a ternary operator. This also means that ternary operators must not be nested. Prefer if/else constructs in these cases.
 + The and and or keywords are banned. It's just not worth it. Always use && and || instead.
 + Prefer `{` and `}` over `do` and `end` for single-line blocks. 
 + Use single-line `if/unless` statements when you have a single-line body.

[The Ruby Style Guide][1]

----------


 Installation: `gem install rubocop`

Usage: `rubocop`
Checks all of the files in the current working directory.
Can take an argument for which file/directory to check.

For example: `rubocop good_name_bad_name.rb`
Returns:

    Inspecting 1 file
    C
    
    Offenses:
    
    good_name_bad_name.rb:3:7: C: Use snake_case for methods.
      def badName
          ^^^^^^^
    good_name_bad_name.rb:9:7: C: Use CamelCase for classes and modules.
    class Bad_name
          ^^^^^^^^
    
    1 file inspected, 2 offenses detected

Note: To use RuboCop in Rails: run `rubocop -R`. Use it like normal but do **NOT** forget the `-R` switch.

Note: 
In some default Rails generators RuboCop gives an error. 

For example:

    app/controllers/scripts_controller.rb:64:3: C: Keep a blank line before and after private.
      private
      ^^^^^^^
    app/controllers/scripts_controller.rb:66:5: C: Inconsistent indentation     detected.
        def set_script
        ^^^^^^^^^^^^^^

And ***192 more!***

----------

Git, Pre-commit and RuboCop
======================


----------

To install pre-commit: run `gem install pre-commit`
To use pre-commit in your current git repo: run `pre-commit install`
For RuboCop to check your repo with pre-commit: run `git config pre-commit.checks "rubocop"`
To see all available checks (optional): run `pre-commit list`

And you are done!

For example when you try to commit with wrong code:

    pre-commit: Stopping commit because of errors.
    Inspecting 1 file
    C
    
    Offenses:

    good_name_bad_name.rb:4:7: C: Use snake_case for methods.
      def badName
          ^^^^^^^
    good_name_bad_name.rb:10:7: C: Use CamelCase for classes and modules.
    class Bad_name
          ^^^^^^^^
    
    1 file inspected, 2 offenses detected
    
    pre-commit: You can bypass this check using `git commit -n`

  [1]: https://github.com/styleguide/ruby

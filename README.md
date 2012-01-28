TestR
=====

Quick and easy [Ruby](http://www.ruby-lang.org/en/)
([Rspec](http://rspec.info/) and
[Test::Unit](http://ruby-doc.org/stdlib-1.9.3/libdoc/test/unit/rdoc/Test/Unit.html))
TDD on [Emacs](http://www.gnu.org/software/emacs/).

Mostly based off [Jim Weirich](https://github.com/jimweirich)
[emacs-setup-esk/testing.el](https://github.com/jimweirich/emacs-setup-esk/blob/master/testing.el).

It also includes toggle.el:

    ;; toggle.el --- quickly open corresponding file (eg test vs impl).
    ;; Copyright (C) 2006-2007 by Ryan Davis
    ;; Author: Ryan Davis <ryand-ruby@zenspider.com>

PS. It has nothing to do with the
[TestR](https://github.com/sunaku/testr) (renamed to
[Tork](https://github.com/sunaku/tork)) project. I just stole the name
:)

## Features:

Quickly:

* jump between {specs,tests} for fast viewing and editing.
* run {specs,tests} files.
* run {specs,tests} methods.

## Installation:

In your emacs config:

    (add-to-list 'load-path "~/.emacs.d/load/path/testr.el")
    (require 'testr)

### noansi

By default it will clear out ansi characters with the executable
`bin/noansi` ruby script. So, you should put it somewhere in your
$PATH. Something like this:

    $ cd testr
    $ cp bin/noansi ~/bin # if ~/bin is in your $PATH

### .env.rc
    
If you would like to define $ENV specific setting to your project you
could add them to an `.env.rc` file in your project root directory.

### .togglerc

If you want to use the toggling functionality you should add a
`.togglerc` file to your project's root directory.

Example -- Set the style only:

    (buffer-toggle-style 'my-project-name)

Example -- Define a mapping and then select it:

    (buffer-toggle-mapping
    '(my-project-name    
      (("test/\\1_test.rb" . "lib/\\1.rb")
      ("\\1_test.rb"      . "\\1.rb"))))
    (buffer-toggle-style 'my-project-name)

For more examples see [jimweirich .togglerc
here](https://github.com/jimweirich/Given/blob/master/.togglerc) or
[mine](https://github.com/jpablobr/ttycoke/blob/master/.togglerc).

Finally:

    M-x testr-mode

or for true TDD:

    (add-hook 'ruby-mode-hook '(lambda () (testr-mode)))

## Usage

### Key binding:

* M-t     => `testr-toggle-buffer`
* C-c tf  => `testr-run-test-file`
* C-c tm  => `testr-run-test-method`
* C-c sf  => `testr-run-spec-file`
* C-c sm  => `testr-run-spec-method`
* C-c rr  => `testr-run-last-test-or-spec-file`
* C-c rm  => `testr-run-last-test-or-spec-method`

### Complete list of functions:

    testr-mode
    testr-code-test-split
    testr-kill-test-buffer
    testr-mark-for-testing
    testr-run-last-test-or-spec-file
    testr-run-last-test-or-spec-method
    testr-run-spec-file
    testr-run-spec-method
    testr-run-test-file
    testr-run-test-functionals
    testr-run-test-integration
    testr-run-test-method
    testr-run-test-or-spec-file
    testr-run-test-or-spec-method
    testr-run-test-rake
    testr-run-test-units
    testr-split-or-toggle
    testr-toggle-buffer
    testr-toggle-clear-buffer-styles
    testr-toggle-warnings

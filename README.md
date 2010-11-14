A  [yasnippet](http://code.google.com/p/yasnippet/) bundle for Emacs [ess-mode](http://ess.r-project.org/).

# Using the header snippet

To expand the header snippet when opening a new ess-mode file, add 
the following code to your init.el file.  This requires the svn
version of yasnippet to work.

    (defun yas/expand-by-uuid (mode uuid)
      "Exapnd snippet template in MODE by its UUID"
      (yas/expand-snippet 
       (yas/template-content 
        (yas/get-template-by-uuid mode uuid))))
    
    (require 'autoinsert)
    (auto-insert-mode)
    (setq auto-insert-query nil)
    (define-auto-insert "\.R" 
      '(lambda () (yas/expand-by-uuid 'ess-mode "header")))
    

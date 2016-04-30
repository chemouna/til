
## Enable Square brackets in Spacemacs

To enable square brackets on spacemacs in .spacemacs file in the dotspacemacs/user-config  
section put :

```elisp
(defun dotspacemacs/user-config ()
  "Configuration function for user code.
This function is called at the very end of Spacemacs initialization after
layers configuration. You are free to put any user code."

  (setq mac-option-modifier nil
        mac-command-modifier 'meta
        x-select-enable-clipboard t)

  )
```  

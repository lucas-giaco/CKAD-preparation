# CKAD exam preparation
Last week I approved the [CKAD](https://www.cncf.io/certification/ckad/) exam and now that I have some free time I want to share some resources and tips that were useful while studying and practicing.

## Resources
First of all, it was really helpful to take a look at the current [exam study guide](https://github.com/cncf/curriculum/blob/master/CKAD_Curriculum_V1.18.pdf) to be aware of the topics included.
During my preparation, I made these exercises over and over again, mostly to get comfortable with the resources that I rarely use
* https://github.com/dgkanatsios/CKAD-exercises
* https://github.com/bbachi/CKAD-Practice-Questions
* https://github.com/bmuschko/ckad-prep

I also took these courses to get some background knowledge and be able to have a deeper understanding of how Kubernetes works under the hoods.
* https://www.edx.org/es/course/introduction-to-kubernetes (Free)
* https://training.linuxfoundation.org/training/kubernetes-for-developers/ (Paid)

Regarding the Linux Foundation course, you may take advantage of a [30% discount](https://training.linuxfoundation.org/april-2020-promo/) that is currently available in the Linux Foundations Training page

## Tips and tricks
These tips helped me to improve speed and performance while taking the exam.
* You won't be allowed to have any apps open but chrome and only with two tabs, one for the exam page and another one with k8s documentation. However, you may have bookmarks with helpful references within the allowed sites.
* **`kubectl run` command only creates pods starting from version 1.18. Deprecated generators for deployments, jobs, and cronjobs were removed**
* I found useful to invest some time at the beginning of the exam to properly set up the terminal:
  - Edit the `.bashrc` and add these aliases and sources:
    ```bash
    alias k='kubectl'
    source <(kubectl completion bash | sed 's/kubectl/k/g') # This enables autocompletion for the alias above
    alias kc='kubectl config set-context --current --namespace '
    alias kx='kubectl explain'
    ```
    Run `source .bashrc` to apply these changes to the current session
  - If you want to change the default editor (vim), you may add `export KUBE_EDITOR=<your_editor>` to the above file
  - If you're used to vim, create/edit the `.vimrc` file with these lines which makes your yaml editing less error-prone:
    ```bash
    set expandtab # use spaces for tabs
    set tabstop=2 # use 2 spaces for tab
    colorscheme desert # I found the default color scheme too hard to read
    ```
* No cheat-sheets allowed, so you must remember the above changes at the exam time
* I found useful switching context namespace before start solving the task. This way you don't need to remember to add  `-n <some_namespace>` to every command
* When no namespace specified, use the `default` namespace
* Use `kubectl edit` only if you're confident about the change you're about to make. Otherwise, kubectl will prompt you again to the editing view
* `--dry-run -o yaml` are really helpful options to avoid writing boilerplate manifests.
* `--export` options is deprecated but still available to generate yaml files from existing resources without cluster-specific information
* Copy-on-select is not available in the web terminal. If you're used to selecting text from the terminal and paste it with right-click this won't work, so remember using `Ctrl+Insert` and `Shift+Insert`.
* Last but not least: practice, practice, practice

### References
* [The CKAD browser terminal](https://codeburst.io/the-ckad-browser-terminal-10fab2e8122e)
* [How To Pass the Certified Kubernetes Application Developer (CKAD) Exam](https://medium.com/bb-tutorials-and-thoughts/how-to-pass-the-certified-kubernetes-application-developer-ckad-exam-503e9562d022)
* [How to beat Kubernetes CKAD certification](https://medium.com/@nassim.kebbani/how-to-beat-kubernetes-ckad-certification-c84bff8d61b1)
* [Webinar: CKA/CKAD](https://www.youtube.com/watch?v=z0VSJPdP674)

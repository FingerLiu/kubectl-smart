# kubectl-smart
A kubectl plugin that makes kubectl smart with name search.Type less letters!Save more life!
![demo](./imgs/kubectl-smart.gif)

# Installation
using curl:
```bash
curl -LO https://github.com/FingerLiu/kubectl-smart/raw/master/kubectl-smart
chmod +x ./kubectl-smart
sudo mv ./kubectl-smart /usr/local/bin/kubectl-smart
kubectl smart -h
```

using krew:
```bash
TODO
kubectl smart -h
```

# Usage

```bash
USAGE:
  smart sub_command [options...] [name_pattern...]
SUB_COMMAND:
  gp                        : shortcut for get pod
  l,logs                    : shortcut for logs
  e,exec                    : shortcut for exec
  edp                       : shortcut for edit pod
  ed,edit                   : shortcut for edit
  dp                        : shortcut for delete pod
  g                         : shortcut for get
  h,help                    : show this message
OPTIONS:
  -n                        : namespace
  -w,--wide                 : TODO get with wide output
  -f,--follow               : follow log output
  --tail                    : tail logs
  -t                        : --tty=true: Stdin is a TTY
  -i                        : --stdin=true: Pass stdin to the container
  -s                        : sort by create datetime
  -c                        : TODO container name.
  -e                        : use exact match rather than grep. Only use this when you want to disable grep when grep return multi items.
Examples:
  # if you installed through krew, you should **kubectl smart** to replace **kubectl s**
  # get pod with name contains my in namespace her-namespace
  # (kubectl get pod -n her-namespace-a |grep my)
  kubectl smart gp -n her.*a my

  # get log for pod with name my
  # (kubectl logs --tail 100 -f $(kubectl get pods | awk '/my/ {print $1;exit}'))
  kubectl smart l my

  # exec into pod
  # kubectl exec -ti my-pod-i3jx bash
  kubectl smart e my bash

  # get deploy with name contains my
  # (kubectl get deploy | grep my)
  kubectl smart g deploy my
```

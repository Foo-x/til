# エディタを開かずにautosquash

`git -c sequence.editor=: rebase -i --autosquash <SHA>` のようにするとエディタを開かずにautosquashできる。  
`GIT_SEQUENCE_EDITOR=: git rebase -i --autosquash <SHA>` でも可。

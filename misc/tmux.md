<!-- TITLE: Tmux -->
<!-- SUBTITLE: A quick summary of Tmux -->

# Config file .tmux.conf


```text
# Toggle mouse on
bind-key M \
  set-option -g mouse on \;\
  display-message 'Mouse: ON'

# Toggle mouse off
bind-key m \
  set-option -g mouse off \;\
  display-message 'Mouse: OFF'

# Sane scrolling
set -g terminal-overrides 'xterm*:smcup@:rmcup@'


```

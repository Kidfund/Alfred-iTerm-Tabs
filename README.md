# Alfred-iTerm-Tabs
Open the iTerm tabs you'll need for development

## Trigger

*kidtabs* in [Alfred](https://www.alfredapp.com/ "Alfred")

Download [here](https://github.com/Kidfund/KidTabs/blob/master/Kidfund%20iTerm%20Dev.alfredworkflow?raw=true "here")

## Tabs

1. iOS project
2. Laravel project. Usually where I run artisan commands
3. Laravel project; Tails most recent file in the log directory. I also jump around from here. Usually CDing to the realm directory to pop it into [Realm Browser](https://github.com/realm/realm-browser-osx "Realm Browser")
4. React project; 

## Script

If you choose to run this [directly from](https://www.iterm2.com/documentation-scripting.html "directly from") iTerm, this is the underlying script. Crude but does the job

```applescript
tell application "iTerm2"
  tell current session of current window
    write text "cd ~/workspace/kidfund/ios/Kidfund"
  end tell
  tell current window
    create tab with default profile
      tell current session of current tab
        write text "cd ~/workspace/kidfund/web"
      end tell
  end tell
    tell current window
    create tab with default profile
      tell current session of current tab
        write text "cd ~/workspace/kidfund/web && tail -f storage/logs/\"$(ls -at storage/logs | head -n 1)\""
      end tell
  end tell
    tell current window
    create tab with default profile
      tell current session of current tab
        write text "cd ~/workspace/kidfund/web-react"
      end tell
  end tell
  tell current window
    create tab with default profile
      tell current session of current tab
        write text "cd ~/workspace/kidfund/automation/ansible"
      end tell
  end tell
end tell
```

# Introduction

I use a combination of Alfred and Karabiner Elements to control my system and applications with 2 main hotkeys. I have a ‘System’ hotkey that performs system-wide tasks, and a ‘App Specific’ hotkey that will perform tasks unique to the currently focussed application. 

# System-wide Tasks

### The System Hotkey

The System hotkey has two main functions:

1. **Open Alfred Instantly**: Press the System hotkey alone to open Alfred.
2. **Hyper Key for Shortcuts**: Hold the System hotkey to use it as a Hyper Key, letting you combine it with other keys for various system-wide tasks.

Some examples:

- **Hyper + H**: Opens Alfred to your home folder.
- **Hyper + C**: Accesses Alfred's Clipboard Manager.
- **Hyper + S**: Shows your snippets.
- **Hyper + V**: Manages your audio settings.
- **Hyper + P**: Returns you to your last used path in Alfred.
- **Hyper + R**: Opens your recent files workflow.

By limiting these to commands useful across all applications, you maintain a clean, efficient system.

# Customized App-specific Commands

### The App Specific Hotkey

Remembering all the hotkeys and commands for different applications can be difficult. My solution is to create app-specific Alfred workflows. When I need a specific function in an app repeatedly, I add it to a tailored Alfred workflow.

With the App Specific hotkey, you can launch a workflow that presents a list of commands tailored to the current application. This can include:

- Issuing hotkeys
- Launching scripts
- Choosing menu items
- Running complex macros built with Alfred's nodes

This allows you to personalize workflows to fit how you use each application.

# Choosing the right keys

## System hotkey

I use Karabiner Elements to create a 'Hyper Key' (Command+Control+Option+Shift simultaneously). Using the Caps Lock key for this is ideal because it's easy to press and not often used otherwise. Regular Caps Lock functionality is still accessible by pressing Shift + Caps Lock.

## App Specific hotkey

This one is nifty. As a modifier key, Command only ever functions when combined with another key (Command+N for ‘new’ etc). So we can use Karabiner Elements again, this time to remap the Command key to ‘something else’ when it is pressed alone. That ‘something else’ becomes the hotkey to launch our App Specific Alfred Workflows (I use F19 for this)

# System setup

## Karabiner Elements config

Set up the following rules in Karabiner Elements

- Caps-Lock, when held, becomes Hyper-Key 
- Caps-Lock, when pressed alone, becomes Hyper-Key + Spacebar 
- Command, when held, remains Command 
- Command, when pressed alone, becomes F19

Follow these steps to configure Karabiner Elements:

1. Install and open Karabiner Elements
2. Go to ‘Complex Modifications’
3. Click ‘Add your own rule’
4. Copy and paste one of the below Gists into the field and click save
5. Repeat for the second rule.

Github Gist’s for each rule 

[Karabiner Elements - Hyper Key Implementation for Alfred](https://gist.github.com/NeighNeighNeigh/544d7dabf0f47036c1b2bbc345ce8477)

[Karabiner Elements - Command to F19 when pressed alone](https://gist.github.com/NeighNeighNeigh/011891a832d8ee7a66c4dd6f1bddccac)

## Alfred Config

Set the main Alfred hotkey

1. Open Alfred Preferences
2. Go to General
3. Set Alfred Hotkey to ⌃⌥⇧⌘+Space. If you’ve already set up Karabiner, you can just press your Hyper-Key here.

# Alfred Workflows integration

## System Hotkey Example

Perhaps you have an Emoji Picker workflow. If you’re like me, Emoji selection is an often used system-wide function. So within Alfred’s preferences, open your Workflow and edit the existing (or create one if required) [Hotkey Trigger Object](https://www.alfredapp.com/help/workflows/triggers/hotkey/). Open the object, enter the Hotkey field and press Hyper-Key + E.

System hotkeys don’t have to be Alfred specific of course, anything on your system that has system-wide hotkeys can be set to use the Hyper-Key.

## App Specific Workflows

Here we make use of Alfred's Hotkey Object's **Related Apps** feature.

From Alfred’s documentation:

> It’s possible to [share hotkeys between multiple workflow triggers](https://www.alfredapp.com/help/workflows/triggers/hotkey/#sharing-hotkeys), and careful use of Related Apps will give you a seamless experience.

So we: 

1) Create a new workflow for each app we want to control.
2) Set the Hotkey Trigger to our App Specific hotkey.
3) Add the app to the ‘Related apps’ filed within the Hotkey Trigger Object. 
4) Use Alfreds tools to create a list of actions specific to that app.

And that's it. In the end you have two hotkeys. One you invoke to adjust systems settings, the other when you need to do something in-app. The hotkeys are easy to reach, and one-hit. It's great!

Since implementing it has really become a joy to use. The clear distinction between system and app related interactions works really well for me. Cheers!

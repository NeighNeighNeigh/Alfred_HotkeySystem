<img width="256" alt="image" src="https://github.com/user-attachments/assets/80f815a5-bbda-4d4f-8966-41561d8edd01"> <img width="256" alt="image" src="https://github.com/user-attachments/assets/8a5f90c3-f176-414c-ab7b-9fbce5c185b1">



# Introduction

I use a combination of [Alfred](https://www.alfredapp.com) and [Karabiner Elements](https://karabiner-elements.pqrs.org) to control my system and applications with 2 main hotkeys. I have a ‘System’ hotkey that performs system-wide tasks, and an ‘App Specific’ hotkey that will perform tasks unique to the currently focussed application. 

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
- **Hyper + arrows**: Window management.

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

I use Karabiner Elements to transform Caps Lock into the 'Hyper Key' (Command+Control+Option+Shift simultaneously). Using the Caps Lock for this is ideal because it's easy to press and not often used otherwise. Regular Caps Lock functionality is still accessible by pressing Shift + Caps Lock.

## App Specific hotkey

This one is _nifty_. As a modifier key, Command only ever functions when combined with another key (Command+N for ‘new’ etc). So we can use Karabiner Elements again, this time to remap the Command key to ‘something else’ when it is pressed alone. That ‘something else’ becomes the hotkey we enter into Alfred to launch our App Specific Alfred Workflows (I use F19 for this).

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

# App Specific Workflow Examples

I have put together 2 example workflows. Both of these are using the [List Filter Input](https://www.alfredapp.com/help/workflows/inputs/list-filter/) to build a menu of options.

## Example App Control - Basic

In the Basic Example, every item in the List Filter is duplicated into a [Conditional Utility](https://www.alfredapp.com/help/workflows/utilities/conditional/) - then these branch into other Alfred features. So selecting the menu item will execute along the relevant branch. If you want a new menu item, you add it to the List Filter, and the Conditional, followed by whatever you want Alfred to actually do. Do note though, I don't use this method, as I find maintaining it too cumbersome.

## Example App Control - Advanced

In the Advanced Example, we still use a List Filter to choose items. But instead of maintaining a Conditional for every single list item, we make use of Alfred's [Split Arg Utility](https://www.alfredapp.com/help/workflows/utilities/split-arg/). In the Arg field of each List Filter item, the first line is used to indicate which branch to follow in the Conditional. The second line (three dashes '---') is used by the Split Args Utility so that everything below will be passed through to the subsequent objects.

This makes maintaining the menu far easier, as most of the work can be done in the List Filter alone. You might have 20 entries in the List Filter, but only 4 branches in the Conditional. Once set up, whenever you want to add a new menu item you just add it to the List Filter, give it a nice name and an icon, and fill out the Arg field as required.

# Conclusion

And that's it. In the end you have two hotkeys. One you invoke to adjust systems settings, the other when you need to do something in-app. The hotkeys are easy to reach, and one-hit. It's great!

Since implementing it has really become a joy to use. The clear distinction between system and app related interactions works really well for me. Cheers!

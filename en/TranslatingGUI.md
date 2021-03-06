---
title: Translating the JabRef Interface
helpCategories: ["Contributing"]
---

# Translating the JabRef Interface

## Introduction

JabRef comes with a set of translations into different languages, currently:
Chinese (simplified), Danish, Dutch, English, Farsi, French, German, Indonesian, Italian, Japanese, Norwegian, Persian, Portuguese (Brazil), Russian, Spanish, Swedish, Turkish and Vietnamese.

If the JabRef interface already exists in your language, you can help improve it.
Otherwise, you can start translating JabRef into your own language.

For each language, there are two files (`xx` denotes the country code for the language):
- `Menu_xx.properties`: translation of menu items
- `JabRef_xx.properties`: translation of the other items

## Improving an existing translation

We use the service of [Crowdin](https://crowdin.com/) to keep our translations updated.
It is a service directly running in the browser and one can quickly join and start translating.
Please visit <http://translate.jabref.org/> to get started.

## Translating JabRef into a new language

Crowdin offers to quickly add a new language.
Please contact us so that we add a new language.

### The property files

In the JabRef source code tree, the property files reside in the [/src/main/resources/l10n](https://github.com/JabRef/jabref/blob/master/src/main/resources/l10n/) directory.
For each language there are twofiles (`xx` denotes the country code for the language):

- `Menu_xx.properties`: translation of menu items, marked up for mnemonic keys
- `JabRef_xx.properties`: translation of the other items

### The format of the property files

Each entry is first given in English, then in the other language, with the two parts separated by an '=' character. For instance, a line can look like this in a German translation file:

`Background\ color\ for\ optional\ fields=Hintergrundfarbe für optionale Felder`

Note that each space character is escaped (`\ `) to make it a valid property key.
The translation value does not need any esacpes.

Some entries contain "variables" that are inserted at runtime by JabRef - this can for instance be a file name or a file type name:

`Synchronizing\ %0\ links...=Synchronisiere %0-Links...`

A variable is denoted by `%0`, `%1`, `%2` etc. In such entries, simply repeat the same notation in the translated version.

As we can see, there are several "special" characters: the percent sign and the equals sign, along with the colon character. If these characters are to be part of the actual text in an entry, they must be escaped in the English version, as with the colon in the following example:

`Error\ writing\ XMP\ to\ file\:_%0=Fehler beim Schreiben von XMP in die Datei: %0`

The character encoding should be **UTF-8**. Please avoid Unicode escaping such as `\u2302`.

#### Testing the translation

For a translation to be available within JabRef, a corresponding line must be added in the Java class GUIGlobals (found in the directory `/src/main/java/org/jabref/logic/l10n/Languages.java` in the JabRef source code tree). The line is inserted in the static {} section where the map LANGUAGES is populated. The code must of course be recompiled after this modification.

To test your translation you must be able to compile the source tree after making your additions.
This requires you to install the [Java Development Kit](http://www.oracle.com/technetwork/java/javase/downloads/index.html).
Execute `gradlew run` in the root directory and JabRef should start.

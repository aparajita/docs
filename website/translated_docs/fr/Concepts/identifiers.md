---
id: identifiers
title: Identifiants
---

This section describes the conventions and rules for naming various elements in the 4D language (variables, object properties, tables, forms, etc.).

> If non-Roman characters are used in the names of the identifiers, their maximum length may be smaller.



## Tableaux

Array names follow the same rules as [variables](#variables).


## Classes

The name of a class can contain up to 31 characters.

A class name must be compliant with standard [property naming rules](#object-properties) for dot notation.

> Giving the same name to a class and a [database table](#tables) is not recommended, in order to prevent any conflict.



## Fonctions

Function names must be compliant with standard [property naming rules](#object-properties) for dot notation.

> **Astuce :** préfixer le nom de la fonction par un trait de soulignement ("_") exclura la fonction des fonctionnalités d'auto-complétion dans l'éditeur de code 4D.



## Propriétés des objets

The name of an object property (also called object *attribute*) can contain up to 255 characters.

Object properties can reference scalar values, ORDA elements, class functions, other objects, etc. Whatever their nature, object property names must follow the following rules **if you want to use the [dot notation](dt_object.md#object-properties)**:

- A property name must begin with a letter, an underscore, or a dollar "$".
- Thereafter, the name can include any letter, digit, the underscore character ("_"), or the dollar character ("$").
- Property names are case sensitive.


Voici quelques exemples :

```4d
monObjet.monAttribut:="10"
 $valeur:=$clientObj.data.address.city
```

> If you use **string notation** within square brackets, property names can contain any characters (ex: `myObject["1. First property"]`).

See also [ECMA Script standard](https://www.ecma-international.org/ecma-262/5.1/#sec-7.6).

## Paramètres

Parameter names must start with a `$` character and follow the same rules as [variable names](#variables).

Voici quelques exemples :

```4d
Function getArea($width : Integer; $height : Integer)-> $area : Integer

#DECLARE ($i : Integer ; $param : Date) -> $myResult : Object
```


## Méthodes

The name of a project method name contain up to 31 characters.

- A project method name must begin with a letter, a digit, or an underscore
- Thereafter, the name can include any letter or digit, the underscore character ("_"), or the space character.
- Do not use reserved names, i.e. 4D command names (`Date`, `Time`, etc), keywords (`If`, `For`, etc.), or constant names (`Euro`, `Black`, `Friday`, etc.).
- Project method names are case insensitive.

Voici quelques exemples :

```4d
If(Nouveau client)
DELETE DUPLICATED VALUES
APPLY TO SELECTION([Employés];AUGMENTER SALARIES)
```

**Conseil :** Nous vous recommandons d'adopter, pour nommer vos méthodes, la même convention que celle utilisée dans le langage de 4D : écrivez les noms de vos procédures en caractères majuscules, et vos fonctions en minuscules avec la première lettre en majuscule. Use uppercase characters for naming your methods; however if a method returns a value, capitalize the first character of its name. Ainsi, lorsque vous rouvrirez un projet au bout de plusieurs mois, vous identifierez immédiatement si une méthode retourne ou non un résultat, en regardant son nom dans la fenêtre de l'Explorateur.

 > When you call a method, you just type its name. However, some 4D built-in commands, such as `ON EVENT CALL`, as well as all plug-in commands, expect the name of a method as a string when a method parameter is passed.

Voici quelques exemples :

```4d
    // Cette commande attend une méthode (fonction) ou une formule
 QUERY BY FORMULA([aTable];Recherche Spéciale)
  // Cette commande attend une méthode (procédure) ou une formule
 APPLY TO SELECTION([Employés];AUGMENTER SALARIES)
  // Mais cette commande attend un nom de méthode
ON EVENT CALL("GERER EVENEMENTS")
```





## Tables et champs

You designate a table by placing its name between brackets: \[...]. You designate a field by first specifying the table to which it belongs (the field name immediately follows the table name).

A table name and field name can contain up to 31 characters.

- A table or field name must begin with a letter, an underscore, or a dollar ("$")
- Le nom peut ensuite contenir des caractères alphabétiques, des caractères numériques, des espaces et des tirets bas (_).
- Do not use reserved names, i.e. 4D command names (`Date`, `Time`, etc), keywords (`If`, `For`, etc.), or constant names (`Euro`, `Black`, `Friday`, etc.).
- Additional rules must be respected when the database must be handled via SQL: only the characters _0123456789abcdefghijklmnopqrstuvwxyz are accepted, and the name must not include any SQL keywords (command, attribute, etc.).


Voici quelques exemples :

```4d
FORM SET INPUT([Clients];"Entry")
ADD RECORD([Letters])
[Orders]Total:=Sum([Line]Amount)
QUERY([Clients];[Clients]Name="Smith")
[Letters]Text:=Capitalize text([Letters]Text)

```

> Giving the same name to a table and a [class](#classes) is not recommended, in order to prevent any conflict.

## Variables

The name of a variable can be up to 31 characters, not including the scope symbols ($ or <>).

- A variable name must begin with a letter, an underscore, or a dollar ("$") for [parameters](parameters.md) and [local variables](variables.md#local-variables), or "<>" for [interprocess variables](variables.md#interprocess-variables).
- A digit as first character is allowed but not recommended, and is not supported by the [`var` declaration syntax](variables.md#using-the-var-keyword).
- Thereafter, the name can include any letter or digit, and the underscore character ("_").
- Space character is allowed but not recommended, and is not supported by the [`var` declaration syntax](variables.md#using-the-var-keyword).
- Do not use reserved names, i.e. 4D command names (`Date`, `Time`, etc), keywords (`If`, `For`, etc.), or constant names (`Euro`, `Black`, `Friday`, etc.).
- Variable names are case insensitive.


Voici quelques exemples :

```4d
For($vlRecord;1;100) //local variable
$vsMyString:="Hello there" //local variable
var $vName; $vJob : Text //local variales 
If(bValidate=1) //process variable
<>vlProcessID:=Current process() //interprocess variable
```

## Other names

In the 4D language, several elements have their names handled as strings: **forms**, **form objects**, **named selections**, **processes**, **sets**, **menu bars**, etc.

Such string names can contain up to 255 characters, not including the "$" or "<>" characters (if any).

- String names can contain any characters.
- String names are case insensitive.

Voici quelques exemples :

```4d
DIALOG([Storage];"Note box"+String($vlStage))
OBJECT SET FONT(*;"Binfo";"Times")
USE NAMED SELECTION([Customers];"Closed")//Process Named Selection
USE NAMED SELECTION([Customers];"<>ByZipcode") //Interprocess Named Selection
    //Starting the global process "Add Customers"
$vlProcessID:=New process("P_ADD_CUSTOMERS";48*1024;"Add Customers")
    //Starting the local process "$Follow Mouse Moves"
$vlProcessID:=New process("P_MOUSE_SNIFFER";16*1024;"$Follow Mouse Moves")
CREATE SET([Customers];"Customer Orders")//Process set
USE SET("<>Deleted Records") //Interprocess set
If(Records in set("$Selection"+String($i))>0) //Client set

```


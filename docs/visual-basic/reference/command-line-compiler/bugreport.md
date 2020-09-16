---
title: -bugreport
ms.date: 03/08/2018
helpviewer_keywords:
- -bugreport compiler option [Visual Basic]
- bugreport compiler option [Visual Basic]
- /bugreport compiler option [Visual Basic]
ms.assetid: e4325406-8dbd-4b48-b311-9ee0799e48bb
ms.openlocfilehash: 4b468b8ee4301693312e9545396f2b9f495f75d8
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90550909"
---
# <a name="-bugreport"></a>-bugreport

Crée un fichier que vous pouvez utiliser lorsque vous consignez un rapport de bogue.

## <a name="syntax"></a>Syntaxe

```console
-bugreport:file
```

## <a name="arguments"></a>Arguments

|Terme|Définition|
|---|---|
|`file`|Obligatoire. Nom du fichier qui doit contenir votre rapport de bogue. Placez le nom de fichier entre guillemets ("") si le nom contient un espace.|

## <a name="remarks"></a>Notes

Les informations suivantes sont ajoutées à `file` :

- Copie de tous les fichiers de code source dans la compilation.

- Liste des options du compilateur utilisées dans la compilation.

- Informations de version sur le compilateur, le common language runtime et le système d’exploitation.

- Les résultats de la compilation, le cas échéant.

- Description du problème auquel vous êtes invité.

- Une description de la façon dont vous pensez que le problème doit être résolu, pour laquelle vous êtes invité à le faire.

Étant donné qu’une copie de tous les fichiers de code source est incluse dans `file` , vous souhaiterez peut-être reproduire l’erreur de code (suspect) dans le programme le plus bref possible.

> [!IMPORTANT]
> L' `-bugreport` option produit un fichier qui contient des informations potentiellement sensibles. Cela comprend l’heure actuelle, la version du compilateur, la version .NET Framework, la version du système d’exploitation, le nom d’utilisateur, les arguments de ligne de commande avec lesquels le compilateur a été exécuté, tout le code source et la forme binaire de tout assembly référencé. Cette option est accessible en spécifiant des options de ligne de commande dans le fichier Web.config pour une compilation côté serveur d’une application ASP.NET. Pour éviter cela, modifiez le fichier Machine.config pour empêcher les utilisateurs de compiler sur le serveur.

Si cette option est utilisée avec `-errorreport:prompt` , `-errorreport:queue` ou `-errorreport:send` , et si votre application rencontre une erreur interne du compilateur, les informations contenues dans `file` sont envoyées à Microsoft Corporation. Ces informations permettront aux ingénieurs Microsoft d’identifier la cause de l’erreur et peuvent contribuer à améliorer la prochaine version de Visual Basic. Par défaut, aucune information n’est envoyée à Microsoft. Toutefois, lorsque vous compilez une application à l’aide de `-errorreport:queue` , qui est activé par défaut, l’application collecte ses rapports d’erreurs. Ensuite, lorsque l’administrateur de l’ordinateur se connecte, le système de création de rapports d’erreurs affiche une fenêtre indépendante qui permet à l’administrateur de transmettre à Microsoft tous les rapports d’erreurs qui se sont produits depuis l’ouverture de session.

> [!NOTE]
> L' `-bugreport` option n’est pas disponible dans l’environnement de développement Visual Studio ; elle est disponible uniquement quand vous compilez à partir de la ligne de commande.

## <a name="example"></a> Exemple

L’exemple suivant compile *T2. vb* et place toutes les informations relatives aux rapports de bogues dans le fichier *Problem.txt*.

```console
vbc -bugreport:problem.txt t2.vb
```

## <a name="see-also"></a>Voir aussi

- [Compilateur de ligne de commande de Visual Basic](index.md)
- [-Debug (Visual Basic)](debug.md)
- [-errorreport](errorreport.md)
- [Exemples de lignes de commande de compilation](sample-compilation-command-lines.md)
- [trustLevel, élément de securityPolicy (Schéma des paramètres ASP.NET)](/previous-versions/dotnet/netframework-4.0/as399f0x(v=vs.100))

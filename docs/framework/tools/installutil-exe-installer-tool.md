---
title: Installutil.exe (outil Installer Tool)
description: Utilisez Installutil.exe, le Outil d’installation. Cet outil vous permet d’installer ou de désinstaller des ressources serveur en exécutant les composants du programme d’installation dans les assemblys spécifiés.
ms.date: 03/30/2017
helpviewer_keywords:
- uninstalling server resources
- removing server resources
- status information for installation
- installation progress reports
- installing server resources
- Installer tool
- Installutil.exe
- files, Installer tool
- progress information for installation
- reporting installation progress
ms.assetid: 3f9d0533-f895-4897-b4ea-528284e0241d
ms.openlocfilehash: 042e5f64a7a863173db9c4e601d3152b0df46d97
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164438"
---
# <a name="installutilexe-installer-tool"></a>Installutil.exe (outil Installer Tool)

L'outil Installer est un utilitaire en ligne de commande qui vous permet d'installer et de désinstaller les ressources serveur en exécutant les composants du programme d'installation dans des assemblys spécifiés. Cet outil fonctionne conjointement avec les classes de l'espace de noms <xref:System.Configuration.Install>.

Cet outil est installé automatiquement avec Visual Studio. Pour exécuter l’outil, utilisez l’invite de commandes développeur pour Visual Studio (ou l’invite de commandes Visual Studio dans Windows 7). Pour plus d'informations, consultez [Invites de commandes](developer-command-prompt-for-vs.md).

À l'invite de commandes, tapez :

## <a name="syntax"></a>Syntaxe

```console
installutil [/u[ninstall]] [options] assembly [[options] assembly] ...
```

## <a name="parameters"></a>Paramètres

|Argument|Description|
|--------------|-----------------|
|`assembly`|Nom de fichier de l'assembly dans lequel exécuter les composants du programme d'installation. Omettez ce paramètre si vous souhaitez spécifier le nom fort de l'assembly à l'aide de l'option `/AssemblyName`.|

<a name="options"></a>

## <a name="options"></a>Options

|Option|Description|
|------------|-----------------|
|`/h[elp]`<br /><br /> -ou-<br /><br /> `/?`|Affiche la syntaxe et les options de commande de l'outil.|
|`/help`*assembly*<br /><br /> -ou-<br /><br /> `/?`*assembly*|Affiche les options supplémentaires reconnues par des programmes d'installation individuels dans l'assembly spécifié, avec la syntaxe et les options de commande d'InstallUtil.exe. Cette option ajoute le texte retourné par la propriété <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> de chaque composant de programme d'installation au texte d'aide d'InstallUtil.exe.|
|`/AssemblyName`«*AssemblyName*<br /><br /> ,Version=*major.minor.build.revision*<br /><br /> ,Culture=*locale*<br /><br /> ,PublicKeyToken=*publicKeyToken*"|Spécifie le nom fort d'un assembly, qui doit être enregistré dans le Global Assembly Cache. Le nom de l'assembly doit être qualifié complet avec la version, la culture et le jeton de clé publique de l'assembly. Le nom qualifié complet doit être placé entre guillemets.<br /><br /> Par exemple, "myAssembly, Culture=neutral, PublicKeyToken=0038abc9deabfle5, Version=4.0.0.0" est un nom d'assembly qualifié complet.|
|`/InstallStateDir=[`*DirectoryName*`]`|Spécifie le répertoire du fichier .InstallState contenant les données utilisées pour désinstaller l'assembly. La valeur par défaut est le répertoire qui contient l'assembly.|
|`/LogFile=`[*nom de fichier*]|Spécifie le nom du fichier journal dans lequel la progression de l'installation est enregistrée. Par défaut, si l'option `/LogFile` est omise, un fichier journal nommé *assemblyname*.InstallLog est créé. Si *filename* est omis, aucun fichier journal n'est généré.|
|`/LogToConsole`={`true`&#124;`false`}|Si la valeur est `true`, affiche la sortie dans la console. Si la valeur est `false`, supprime la sortie dans la console.|
|`/ShowCallStack`|Sort la pile des appels dans le journal si une exception se produit à tout moment de l'installation.|
|`/u`[`ninstall`]|Désinstalle les assemblys spécifiés. À la différence des autres options, `/u` s'applique à tous les assemblys, quel que soit l'endroit où l'option apparaît sur la ligne de commande.|

<a name="cmdline"></a>

## <a name="additional-installer-options"></a>Options supplémentaires du programme d'installation

Les programmes d'installation utilisés avec un assembly peuvent reconnaître les options en plus de celles répertoriées dans la section [Options](#options). Pour plus d'informations sur ces options, exécutez InstallUtil.exe avec les chemins d'accès des assemblys sur la ligne de commande avec l'option `/?` ou `/help`. Pour spécifier ces options, ajoutez-les sur la ligne de commande avec les options identifiées par InstallUtil.exe.

> [!NOTE]
> Le texte d'aide sur les options prises en charge par les différents composants du programme d'installation est retourné par la propriété <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType>. Les différentes options qui ont été entrées dans la ligne de commande sont accessibles par programmation depuis la propriété <xref:System.Configuration.Install.Installer.Context%2A?displayProperty=nameWithType>.

Tous les paramètres de ligne de commande et options sont écrits dans le fichier journal de l'installation. Toutefois, si vous utilisez le paramètre `/Password` reconnu par certains composants du programme d'installation, les informations de mot de passe seront remplacées par huit astérisques (*) et n'apparaîtront pas dans le fichier journal.

> [!IMPORTANT]
> Dans certains cas, les paramètres passés au programme d'installation peuvent comprendre des informations sensibles ou personnellement identifiables qui, par défaut, sont écrites dans un fichier journal de texte brut. Pour empêcher ce comportement, vous pouvez supprimer le fichier journal en spécifiant `/LogFile=` (sans l'argument *filename*) après Installutil.exe sur la ligne de commande.

## <a name="remarks"></a>Notes

Les applications .NET Framework comportent des fichiers programme traditionnels et des ressources associées, comme les files d'attente de messages, les journaux des événements et les compteurs de performance qui doivent être créés lors du déploiement de l'application. Vous pouvez utiliser les composants du programme d'installation d'un assembly pour créer ces ressources lors de l'installation de l'application et les supprimer lors de la désinstallation de l'application. Installutil.exe détecte et exécute les composants de ce programme d'installation.

Vous pouvez spécifier plusieurs assemblys sur la même ligne de commande. Toute option précédant le nom d'un assembly s'applique à l'installation de cet assembly. À l'exception de `/u` et `/AssemblyName`, les options sont cumulatives mais remplaçables. Autrement dit, les options spécifiées pour un assembly s'appliquent à tous les assemblys suivants, à moins que l'option ne soit spécifiée avec une nouvelle valeur.

Si vous exécutez Installutil.exe par rapport à un assembly sans spécifier d'options, les trois fichiers suivants seront alors placés dans le répertoire de cet assembly :

- InstallUtil.InstallLog : contient une description générale de la progression de l'installation.

- *assemblyname*.InstallLog : Contient des informations propres à la phase de validation du processus d'installation. Pour plus d'informations sur la phase de validation, consultez la méthode <xref:System.Configuration.Install.Installer.Commit%2A>.

- *assemblyname*.InstallState : Contient les données utilisées pour désinstaller l'assembly.

Installutil.exe utilise la réflexion pour inspecter les assemblys spécifiés et récupérer tous les types <xref:System.Configuration.Install.Installer> dont l'attribut <xref:System.ComponentModel.RunInstallerAttribute?displayProperty=nameWithType> est défini sur `true`. L'outil exécute alors soit la méthode <xref:System.Configuration.Install.Installer.Install%2A?displayProperty=nameWithType>, soit la méthode <xref:System.Configuration.Install.Installer.Uninstall%2A?displayProperty=nameWithType> sur chaque instance du type <xref:System.Configuration.Install.Installer>. Installutil.exe exécute l'installation sous une forme transactionnelle. En cas d'échec de l'installation de l'un des assemblys, l'installation de tous les autres assemblys est restaurée. La désinstallation ne fonctionne pas de manière transactionnelle.

Installutil.exe ne peut pas installer ou désinstaller les assemblys dont la signature est différée, mais il peut installer ou désinstaller des assemblys à nom fort.

Depuis le .NET Framework version 2.0, la version 32 bits du Common Language Runtime (CLR) est fournie uniquement avec la version 32 bits de l'outil Installer, mais la version 64 bits du CLR est fournie avec les versions 32 bits et 64 bits de l'outil Installer. Lorsque vous utilisez la version 64 bits du CLR, utilisez l'outil Installer 32 bits pour installer des assemblys 32 bits et l'outil Installer 64 bits pour les assemblys 64 bits et Microsoft Intermediate Language (MSIL). Les deux versions de l'outil Installer ont le même comportement.

Vous ne pouvez pas utiliser Installutil.exe pour déployer un service Windows qui a été créé à l'aide de C++, car Installutil.exe ne peut pas identifier du code natif incorporé généré par le compilateur C++. Si vous tentez de déployer un service Windows créé à l'aide de C++ avec Installutil.exe, une exception telle que <xref:System.BadImageFormatException> est levée. Pour utiliser ce scénario, déplacez le code de service dans un module C++, puis écrivez l'objet de programme d'installation en C# ou Visual Basic.

## <a name="examples"></a>Exemples

La commande suivante affiche une description de la syntaxe de la commande et des options de InstallUtil.exe.

```console
installutil /?
```

La commande suivante affiche une description de la syntaxe de la commande et des options de InstallUtil.exe. Elle affiche également une description et une liste d’options prises en charge par les composants du programme d’installation dans `myAssembly.exe` si le texte d’aide a été assigné à la propriété <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> du programme d’installation.

```console
installutil /? myAssembly.exe
```

La commande suivante exécute les composants du programme d'installation dans l'assembly `myAssembly.exe`.

```console
installutil myAssembly.exe
```

La commande suivante exécute les composants du programme d'installation dans un assembly à l'aide du commutateur `/AssemblyName` et un nom qualifié complet.

```console
installutil /AssemblyName "myAssembly, Culture=neutral, PublicKeyToken=0038abc9deabfle5, Version=4.0.0.0"
```

La commande suivante exécute les composants du programme d'installation dans un assembly spécifié par le nom de fichier et dans un assembly spécifié par le nom fort. Notez que tous les assemblys spécifiés par le nom de fichier doivent précéder les assemblys spécifiés par le nom fort sur la ligne de commande, car l'option `/AssemblyName` ne peut pas être remplacée.

```console
installutil myAssembly.exe /AssemblyName "myAssembly, Culture=neutral, PublicKeyToken=0038abc9deabfle5, Version=4.0.0.0"
```

La commande suivante exécute les composants du programme de désinstallation dans l'assembly `myAssembly.exe`.

```console
installutil /u myAssembly.exe
```

La commande suivante exécute les composants du programme de désinstallation dans les assemblys `myAssembly1.exe` et `myAssembly2.exe`.

```console
installutil myAssembly1.exe /u myAssembly2.exe
```

Étant donné que la position de l'option `/u` sur la ligne de commande n'est pas importante, cela est équivalent à la commande suivante.

```console
installutil /u myAssembly1.exe myAssembly2.exe
```

La commande suivante exécute les programmes d'installation dans l'assembly `myAssembly.exe` et spécifie l'écriture des informations sur la progression dans `myLog.InstallLog`.

```console
installutil /LogFile=myLog.InstallLog myAssembly.exe
```

La commande suivante exécute les programmes d'installation dans l'assembly `myAssembly.exe`, spécifie que les informations de progression doivent être écrites dans `myLog.InstallLog` et utilise l'option `/reg` personnalisée des programmes d'installation pour spécifier que les mises à jour doivent être effectuées dans le Registre système.

```console
installutil /LogFile=myLog.InstallLog /reg=true myAssembly.exe
```

La commande suivante exécute les programmes d'installation dans l'assembly `myAssembly.exe`, utilise l'option `/email` personnalisée du programme d'installation pour spécifier l'adresse de messagerie de l'utilisateur et supprime la sortie du fichier journal.

```console
installutil /LogFile= /email=admin@mycompany.com myAssembly.exe
```

La commande suivante écrit la progression de l'installation de `myAssembly.exe` dans `myLog.InstallLog` et celle de `myTestAssembly.exe` dans `myTestLog.InstallLog`.

```console
installutil /LogFile=myLog.InstallLog myAssembly.exe /LogFile=myTestLog.InstallLog myTestAssembly.exe
```

## <a name="see-also"></a>Voir aussi

- <xref:System.Configuration.Install>
- [outils](index.md)
- [Invites de commandes](developer-command-prompt-for-vs.md)

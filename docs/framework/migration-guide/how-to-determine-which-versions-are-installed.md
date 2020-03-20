---
title: déterminer les versions du .NET Framework installées
description: Utilisez le code, regedit.exe, ou PowerShell pour détecter quelles versions de .NET Framework sont installées sur une machine en interrogeant le registre Windows.
ms.date: 02/03/2020
dev_langs:
- csharp
- vb
ms.custom: updateeachrelease
helpviewer_keywords:
- versions, determining for .NET Framework
- .NET Framework, determining version
ms.assetid: 40a67826-e4df-4f59-a651-d9eb0fdc755d
ms.openlocfilehash: 8469f977c6ed9691c81a2a8354935557b5c27171
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "77093827"
---
# <a name="how-to-determine-which-net-framework-versions-are-installed"></a>Guide pratique pour déterminer les versions du .NET Framework installées

Les utilisateurs peuvent [installer](../install/index.md) et exécuter plusieurs versions du cadre .NET sur leurs ordinateurs. Quand vous développez ou déployez votre application, vous pouvez avoir besoin de savoir quelles versions de .NET Framework sont installées sur l'ordinateur de l'utilisateur. Le registre contient une liste des versions .NET Framework installées sur un ordinateur.

Le .NET Framework comporte deux principaux composants, dont les versions sont définies séparément :

- Un jeu d'assemblys, qui correspondent aux collections de types et de ressources qui fournissent les fonctionnalités de vos applications. .NET Framework et les assemblys partagent le même numéro de version. Par exemple, 4.5, 4.6.1 et 4.7.2 sont des versions de .NET Framework.

- Le Common Language Runtime (CLR), qui gère et exécute le code de votre application. En règle générale, une version particulière du CLR prend en charge plusieurs versions du .NET Framework. Par exemple, version CLR 4.0.30319. *xxxxxx* où *xxxxx* est inférieur à 42000, prend en charge les versions .NET Framework 4 à 4.5.2. La version CLR supérieure ou égale à 4.0.30319.42000 prend en charge les versions cadres .NET à partir de .NET Framework 4.6.

Des outils entretenus par la communauté sont disponibles pour aider à détecter les versions cadre .NET installées :

- [https://github.com/jmalarcon/DotNetVersions](https://github.com/jmalarcon/DotNetVersions)

  Un outil de ligne de commande .NET 2.0.

- [https://github.com/EliteLoser/DotNetVersionLister](https://github.com/EliteLoser/DotNetVersionLister)

  Un module PowerShell 2.0.

Pour plus d’informations sur la détection des mises à jour installées pour chaque version du cadre .NET, voir [comment déterminer quelles mises à jour cadre .NET sont installées](how-to-determine-which-net-framework-updates-are-installed.md).

## <a name="detect-net-framework-45-and-later-versions"></a>Détecter .NET Framework 4.5 et versions ultérieures

La version de .NET Framework (4.5 et plus tard) installée sur une machine est répertoriée dans le registre à **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full**. Si le sous-clé **complet** est manquant, alors .NET Framework 4.5 ou plus n’est pas installé.

> [!NOTE]
> La sous-clé **de configuration de cadre NET** dans la voie du registre ne commence *pas* par une période.

La valeur REG_DWORD de **la version** du registre représente la version du cadre .NET installé.

<a name="version_table"></a>

| Version du .NET Framework | Valeur de la **libération** |
| ---------------------- | -------------------------- |
| .NET Framework 4.5     | Tous les systèmes d’exploitation Windows: 378389 |
| .NET Framework 4.5.1   | Sur Windows 8.1 et Windows Server 2012 R2: 378675<br />Sur tous les autres systèmes d’exploitation Windows: 378758 |
| .NET Framework 4.5.2   | Tous les systèmes d’exploitation Windows: 379893 |
| .NET Framework 4.6     | Sur Windows 10: 393295<br />Sur tous les autres systèmes d’exploitation Windows: 393297 |
| .NET Framework 4.6.1   | Sur les systèmes Windows intégrant la mise à jour du 10 novembre : 394254<br />Sur tous les autres systèmes d’exploitation Windows (y compris Windows 10): 394271 |
| .NET Framework 4.6.2   | Sur les systèmes Mise à jour anniversaire Windows 10 et Windows Server 2016 : 394802<br />Sur tous les autres systèmes d’exploitation Windows (y compris les autres systèmes d’exploitation Windows 10) : 394806 |
| .NET Framework 4.7     | Sur Windows 10 Creators Update : 460798<br />Sur tous les autres systèmes d’exploitation Windows (y compris les autres systèmes d’exploitation Windows 10) : 460805 |
| .NET Framework 4.7.1   | Sur Windows 10 Fall Creators Update et Windows Server, version 1709: 461308<br/>Sur tous les autres systèmes d’exploitation Windows (y compris les autres systèmes d’exploitation Windows 10) : 461310 |
| .NET Framework 4.7.2   | Sur Windows 10 Avril 2018 Mise à jour et Windows Server, version 1803: 461808<br/>Sur tous les systèmes d’exploitation Windows autres que Windows 10 Avril 2018 Mise à jour et Windows Server, version 1803: 461814 |
| .NET Framework 4.8     | Sur Windows 10 Mai 2019 Mise à jour et Windows 10 Novembre 2019 Mise à jour: 528040<br/>Sur Windows 10 et Windows Server, version 1909: 528209<br/>Sur tous les autres systèmes d’exploitation Windows (y compris les autres systèmes d’exploitation Windows 10) : 528049 |

### <a name="minimum-version"></a>Version minimale

Pour déterminer si une version *minimale* du cadre .NET est présente, utilisez la plus petite valeur de **REG_DWORD version** pour cette version du tableau précédent.

Par exemple, si votre application s’exécute sous .NET Framework 4.8 ou une version ultérieure, testez une valeur **de REG_DWORD** de version supérieure ou *égale à* 528040.

| Version du .NET Framework | Valeur minimale |
| ---------------------- | ------------- |
| .NET Framework 4.5     | 378389 |
| .NET Framework 4.5.1   | 378675 |
| .NET Framework 4.5.2   | 379893 |
| .NET Framework 4.6     | 393295 |
| .NET Framework 4.6.1   | 394254 |
| .NET Framework 4.6.2   | 394802 |
| .NET Framework 4.7     | 460798 |
| .NET Framework 4.7.1   | 461308 |
| .NET Framework 4.7.2   | 461808 |
| .NET Framework 4.8     | 528040 |

### <a name="use-registry-editor"></a>Utiliser l’éditeur de registre

01. À partir du menu **Démarrer**, choisissez **Exécuter**, entrez *regedit*, puis sélectionnez **OK**.

    Vous devez disposer d’informations d’identification d’administrateur pour exécuter regedit.

01. Dans le rédacteur en chef du registre, ouvrez le sous-clé suivant : **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full**. Si la sous-clé **Full** est absente, alors .NET Framework 4.5 n’est pas installé ni une version ultérieure.

01. Vérifiez pour une entrée REG_DWORD nommée **Release**. S’il existe, alors vous avez .NET Framework 4.5 ou plus tard installé. Sa valeur correspond à une version particulière du cadre .NET. Dans le chiffre suivant, par exemple, la valeur de **l’entrée de version** est 528040, qui est la clé de sortie pour .NET Framework 4.8.

    ![Entrée de registre pour le cadre .NET 4.5](./media/clr-installdir.png "Entrée de registre pour le cadre .NET 4.5")

### <a name="use-powershell-to-check-for-a-minimum-version"></a>Utilisez PowerShell pour vérifier une version minimale

Utilisez les commandes PowerShell pour vérifier la valeur de **l’entrée** de sortie de la **HKEY_LOCAL_MACHINE\\\\SOFTWARE Microsoft\\NET Framework Setup\\NDP\\v4\\Full** subkey.

Les exemples suivants vérifient la valeur de l’entrée **Release** pour déterminer si .NET Framework 4.6.2 ou une version ultérieure sont installés. Ce code retourne `True` s’il est installé et `False` dans le cas contraire.

```PowerShell
(Get-ItemProperty "HKLM:SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full").Release -ge 394802
```

### <a name="query-the-registry-using-code"></a>Requête du registre à l’aide du code

01. Utilisez <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A?displayProperty=nameWithType> le <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A?displayProperty=nameWithType> et les méthodes pour accéder à la **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full** subkey dans le registre Windows.

    > [!IMPORTANT]
    > Si l’application que vous exécutez est 32 bits et en cours d’exécution dans Windows 64 bits, les chemins de registre seront différents de ceux précédemment énumérés. Le registre 64 bits est disponible dans le **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\ ** subkey. Par exemple, le sous-clé de registre pour .NET Framework 4.5 est **HKEY_LOCAL_MACHINE\\\\SOFTWARE\\\\Wow6432Node\\Microsoft\\NET Framework Setup NDP v4\\Full**.

01. Vérifiez la **valeur de REG_DWORD de sortie** pour déterminer la version installée. Pour être compatible, recherchez une valeur supérieure ou égale à la valeur listée dans le [tableau des versions du .NET Framework](#version_table).

L’exemple suivant vérifie la valeur de l’entrée **Release** dans le Registre pour identifier les versions 4.5 et ultérieures du .NET Framework installées :

[!code-csharp[ListVersions#5](../../../samples/snippets/csharp/framework/migration-guide/versions-installed3.cs)]
[!code-vb[ListVersions#5](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed3.vb)]

Cet exemple suit la pratique recommandée concernant la vérification de version :

- Il vérifie si la valeur de l’entrée **Release** est *supérieure ou égale à* la valeur des clés de version connues.
- Il effectue sa vérification en partant de la version la plus récente vers la version la plus ancienne.

## <a name="detect-net-framework-10-through-40"></a>Détecter .NET Framework 1.0 à 4.0

Chaque version de .NET Framework de 1.1 à 4.0 est répertoriée comme un sous-clé à **\\HKEY_LOCAL_MACHINE SOFTWARE\\Microsoft\\NET Framework Setup\\NDP**. Le tableau suivant répertorie le chemin vers chaque version cadre .NET. Pour la plupart des versions, il ya `1` une **installation** REG_DWORD valeur de pour indiquer cette version est installée. Dans ces sous-clés, il ya aussi une **version** REG_SZ valeur qui contient une chaîne de version.

> [!NOTE]
> La sous-clé **de configuration de cadre NET** dans la voie du registre ne commence *pas* par une période.

| Version cadre  | Registre Subkey | Valeur |
| ------------------ | --------------- | ----- |
| 1.0                | **Logiciel HKLM\\\\Microsoft\\. NetFramework\\\\Policy v1.0\\3705**     | **Installer** REG_SZ égale`1` |
| 1.1                | **HKLM\\\\Software\\Microsoft\\NET\\Framework Setup NPD v1.1.4322**   | **Installer** REG_DWORD égale`1` |
| 2                | **HKLM\\\\Software\\Microsoft\\NET\\Framework Setup NDP v2.0.50727**  | **Installer** REG_DWORD égale`1` |
| 3.0                | **HKLM\\\\Software\\Microsoft\\NET\\Framework Setup\\NDP v3.0 Configuration** | **InstallSuccess** REG_DWORD égale`1` |
| 3,5                | **HKLM\\\\Software\\Microsoft\\NET\\Framework Setup NDP v3.5**        | **Installer** REG_DWORD égale`1` |
| 4.0 Profil client | **HKLM\\\\Software\\Microsoft\\NET\\Framework\\Setup NPD v4 Client**  | **Installer** REG_DWORD égale`1` |
| 4.0 Profil complet   | **HKLM\\\\Software\\Microsoft\\NET\\Framework\\Setup NDP v4 Complet**    | **Installer** REG_DWORD égale`1` |

> [!IMPORTANT]
> Si l’application que vous exécutez est 32 bits et en cours d’exécution dans Windows 64 bits, les chemins de registre seront différents de ceux précédemment énumérés. Le registre 64 bits est disponible dans le **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\ ** subkey. Par exemple, le sous-clé de registre pour .NET Framework 3.5 est **HKEY_LOCAL_MACHINE\\SOFTWARE\\\\Wow6432Node\\Microsoft\\NET Framework Setup\\NDP v3.5**.

Notez que le chemin du registre vers le sous-marin .NET Framework 1.0 est différent des autres.

### <a name="use-registry-editor-older-framework-versions"></a>Utiliser l’éditeur de registre (anciennes versions-cadres)

01. À partir du menu **Démarrer**, choisissez **Exécuter**, entrez *regedit*, puis sélectionnez **OK**.

    Vous devez disposer d’informations d’identification d’administrateur pour exécuter regedit.

01. Ouvrez la sous-clé qui correspond à la version que vous souhaitez vérifier. Utilisez la table dans le [cadre Détecter .NET 1.0 à 4.0](#detect-net-framework-10-through-40) section.

    Le chiffre suivant montre la valeur sous-clé et sa **version** pour .NET Framework 3.5.

    ![L’entrée du registre pour le cadre .NET 3.5.](./media/net-4-and-earlier.png ".NET Framework 3.5 et versions antérieures")

### <a name="query-the-registry-using-code-older-framework-versions"></a>Requête du registre à l’aide du code (anciennes versions-cadres)

Utilisez <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> la classe pour accéder à la **sous-clé HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NPD** dans le registre Windows.

> [!IMPORTANT]
> Si l’application que vous exécutez est 32 bits et en cours d’exécution dans Windows 64 bits, les chemins de registre seront différents de ceux précédemment énumérés. Le registre 64 bits est disponible dans le **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\ ** subkey. Par exemple, le sous-clé de registre pour .NET Framework 3.5 est **HKEY_LOCAL_MACHINE\\SOFTWARE\\\\Wow6432Node\\Microsoft\\NET Framework Setup\\NDP v3.5**.

L’exemple suivant trouve les versions .NET Framework 1 à 4 qui sont installées :

[!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed1.cs)]
[!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed1.vb)]

## <a name="find-clr-versions"></a>Identifier les versions du CLR

Le .NET Framework CLR installé avec .NET Framework est version séparément. Il existe deux façons de détecter la version du .NET Framework CLR :

- **L’outil Clrver.exe**

  Utilisez [l’outil CLR Version (Clrver.exe)](../tools/clrver-exe-clr-version-tool.md) pour déterminer quelles versions du CLR sont installées sur un ordinateur. Ouvrez [l’invite de commande de développeur pour Visual Studio](../tools/developer-command-prompt-for-vs.md) et entrez `clrver`.

  Exemple de sortie :

  ```console
  Versions installed on the machine:
  v2.0.50727
  v4.0.30319
  ```

- **La `Environment` classe**

  > [!IMPORTANT]
  > Pour .NET Framework 4.5 et les versions <xref:System.Environment.Version%2A?displayProperty=nameWithType> ultérieures, n’utilisez pas la propriété pour détecter la version du CLR. Au lieu de cela, interroger le registre tel que décrit dans [Detect .NET Framework 4.5 et versions ultérieures](#detect-net-framework-45-and-later-versions).
  
  01. Interrogez la propriété <xref:System.Environment.Version?displayProperty=nameWithType> pour récupérer un objet <xref:System.Version>.
  
      L’objet `System.Version` retourné identifie la version du runtime qui est en train d’exécuter le code. Il ne retourne pas les versions d’assembly ni d’autres versions du runtime susceptibles d’avoir été installées sur l’ordinateur.
  
      Pour les versions cadre .NET 4, 4.5, 4.5.1 et 4.5.2, la représentation de la chaîne de l’objet retourné <xref:System.Version> a la forme 4.0.30319. *xxxxx*, où *xxxxx* est inférieur à 42000. Pour .NET Framework 4.6 et les versions ultérieures, il a le formulaire 4.0.30319.42000.
  
  01. Après avoir l’objet **Version,** demandez-le comme suit :
  
      - Pour l’identificateur de la version majeure (par exemple, *4* pour la version 4.0), utilisez la propriété <xref:System.Version.Major%2A?displayProperty=nameWithType>.
  
      - Pour l’identificateur de la version mineure (par exemple, *0* pour la version 4.0), utilisez la propriété <xref:System.Version.Minor%2A?displayProperty=nameWithType>.
  
      - Pour la chaîne de la version entière (par exemple, *4.0.30319.18010*), utilisez la méthode <xref:System.Version.ToString%2A?displayProperty=nameWithType>. Cette méthode retourne une valeur unique qui reflète la version du runtime qui est en train d’exécuter le code. Elle ne retourne pas les versions d’assembly ni d’autres versions du runtime susceptibles d’être installées sur l’ordinateur.

  L’exemple suivant utilise la propriété <xref:System.Environment.Version%2A?displayProperty=nameWithType> pour récupérer les informations de version du CLR :
  
  [!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed2.cs)]
  [!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed2.vb)]

## <a name="see-also"></a>Voir aussi

- [Comment : Déterminer quelles mises à jour du cadre .NET sont installées](how-to-determine-which-net-framework-updates-are-installed.md)
- [Installer le .NET Framework pour les développeurs](../install/guide-for-developers.md)
- [.NET Versions et dépendances du Cadre](versions-and-dependencies.md)

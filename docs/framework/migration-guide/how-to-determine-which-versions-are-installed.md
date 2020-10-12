---
title: déterminer les versions du .NET Framework installées
description: Utilisez du code, regedit.exe ou PowerShell pour détecter les versions de .NET Framework qui sont installées sur un ordinateur en interrogeant le Registre Windows.
ms.date: 02/03/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- versions, determining for .NET Framework
- .NET Framework, determining version
ms.assetid: 40a67826-e4df-4f59-a651-d9eb0fdc755d
ms.openlocfilehash: faeb2c14b9c1d93b558c67a42c223702178407c0
ms.sourcegitcommit: b59237ca4ec763969a0dd775a3f8f39f8c59fe24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2020
ms.locfileid: "91955588"
---
# <a name="how-to-determine-which-net-framework-versions-are-installed"></a>Guide pratique pour déterminer les versions du .NET Framework installées

Les utilisateurs peuvent [installer](../install/index.md) et exécuter plusieurs versions de .NET Framework sur leurs ordinateurs. Lorsque vous développez ou déployez votre application, vous devrez peut-être connaître les versions de .NET Framework qui sont installées sur l’ordinateur de l’utilisateur. Le registre contient une liste des versions de .NET Framework installées sur l’ordinateur.

.NET Framework se compose de deux composants principaux, dont les versions sont gérées séparément :

- Un jeu d'assemblys, qui correspondent aux collections de types et de ressources qui fournissent les fonctionnalités de vos applications. .NET Framework et les assemblys partagent le même numéro de version. Par exemple, 4.5, 4.6.1 et 4.7.2 sont des versions de .NET Framework.

- Le Common Language Runtime (CLR), qui gère et exécute le code de votre application. En règle générale, une version particulière du CLR prend en charge plusieurs versions du .NET Framework. Par exemple, CLR version 4.0.30319. *xxxxx* où *xxxxx* est inférieur à 42000, prend en charge .NET Framework les versions 4 à 4.5.2. La version CLR supérieure ou égale à 4.0.30319.42000 prend en charge les versions .NET Framework à partir de .NET Framework 4,6.

Des outils gérés par la Communauté sont disponibles pour vous aider à détecter les versions de .NET Framework installées :

- [https://github.com/jmalarcon/DotNetVersions](https://github.com/jmalarcon/DotNetVersions)

  Outil en ligne de commande .NET 2,0.

- [https://github.com/EliteLoser/DotNetVersionLister](https://github.com/EliteLoser/DotNetVersionLister)

  Un module PowerShell 2,0.

Pour plus d’informations sur la détection des mises à jour installées pour chaque version de .NET Framework, consultez [Comment : déterminer les mises à jour de .NET Framework installées](how-to-determine-which-net-framework-updates-are-installed.md).

## <a name="detect-net-framework-45-and-later-versions"></a>Détection des .NET Framework 4,5 et versions ultérieures

La version de .NET Framework (4,5 et versions ultérieures) installée sur un ordinateur est listée dans le registre à l’adresse **HKEY_LOCAL_MACHINE \\ logiciel \\ Microsoft \\ NET Framework installation \\ NDP \\ v4 \\ Full**. Si la sous-clé **complète** est manquante, .NET Framework 4,5 ou version ultérieure n’est pas installé.

> [!NOTE]
> La sous-clé **d’installation** du .NET Framework dans le chemin d’accès du registre ne commence *pas* par un point.

La valeur de REG_DWORD de **version** dans le registre représente la version de .NET Framework installée.

<a name="version_table"></a>

| Version du .NET Framework | Valeur de la **mise en version** |
| ---------------------- | -------------------------- |
| .NET Framework 4.5     | Tous les systèmes d’exploitation Windows : 378389 |
| .NET Framework 4.5.1   | Sur Windows 8.1 et Windows Server 2012 R2:378675<br />Sur tous les autres systèmes d’exploitation Windows : 378758 |
| .NET Framework 4.5.2   | Tous les systèmes d’exploitation Windows : 379893 |
| .NET Framework 4.6     | Sur Windows 10:393295<br />Sur tous les autres systèmes d’exploitation Windows : 393297 |
| .NET Framework 4.6.1   | Sur les systèmes Windows intégrant la mise à jour du 10 novembre : 394254<br />Sur tous les autres systèmes d’exploitation Windows (y compris Windows 10) : 394271 |
| .NET Framework 4.6.2   | Sur les systèmes Mise à jour anniversaire Windows 10 et Windows Server 2016 : 394802<br />Sur tous les autres systèmes d’exploitation Windows (y compris les autres systèmes d’exploitation Windows 10) : 394806 |
| .NET Framework 4.7     | Sur Windows 10 Creators Update : 460798<br />Sur tous les autres systèmes d’exploitation Windows (y compris les autres systèmes d’exploitation Windows 10) : 460805 |
| .NET Framework 4.7.1   | Sur Windows 10 automne Creators Update et Windows Server, version 1709:461308<br/>Sur tous les autres systèmes d’exploitation Windows (y compris les autres systèmes d’exploitation Windows 10) : 461310 |
| .NET Framework 4.7.2   | Sur Windows 10 avril 2018 mise à jour et Windows Server, version 1803:461808<br/>Sur tous les systèmes d’exploitation Windows autres que Windows 10 avril 2018 Update et Windows Server, version 1803:461814 |
| .NET Framework 4.8     | Sur Windows 10 mai 2019 mise à jour et Windows 10 novembre 2019 mise à jour : 528040<br/>Sur Windows 10 mai 2020 mise à jour : 528372<br/>Sur tous les autres systèmes d’exploitation Windows (y compris les autres systèmes d’exploitation Windows 10) : 528049 |

### <a name="minimum-version"></a>Version minimale

Pour déterminer si une version *minimale* de .NET Framework est présente, utilisez la plus petite valeur **de REG_DWORD de version pour** cette version à partir du tableau précédent.

Par exemple, si votre application s’exécute sous .NET Framework 4,8 ou une version ultérieure, testez une valeur de REG_DWORD de **mise en sortie** *supérieure ou égale à* 528040.

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

### <a name="use-registry-editor"></a>Utiliser l’éditeur du Registre

01. À partir du menu **Démarrer**, choisissez **Exécuter**, entrez *regedit*, puis sélectionnez **OK**.

   (Vous devez disposer d’informations d’identification d’administration pour exécuter regedit.)

01. Dans l’éditeur du Registre, ouvrez la sous-clé suivante : **HKEY_LOCAL_MACHINE \\ logiciel \\ Microsoft \\ NET Framework installation \\ NDP \\ v4 \\ Full**. Si la sous-clé **complète** n’est pas présente, vous n’avez pas .NET Framework 4,5 ou une version ultérieure installée.

01. Recherchez une entrée de REG_DWORD nommée **Release**. S’il existe, .NET Framework 4,5 ou version ultérieure est installé. Sa valeur correspond à une version particulière de .NET Framework. Dans l’illustration suivante, par exemple, la valeur de l’entrée de **version** est 528040, qui est la clé de mise en version de .NET Framework 4,8.

   ![Entrée de Registre pour .NET Framework 4,5](./media/clr-installdir.png )

### <a name="use-powershell-to-check-for-a-minimum-version"></a>Utiliser PowerShell pour vérifier la version minimale

Utilisez les commandes PowerShell pour vérifier la valeur de l’entrée de **publication** de l’HKEY_LOCAL_MACHINE sous-clé complète de l' **installation du \\ logiciel \\ Microsoft \\ NET Framework, \\ NDP \\ v4 \\ ** .

Les exemples suivants vérifient la valeur de l’entrée de **mise en sortie** pour déterminer si .NET Framework 4.6.2 ou version ultérieure est installé. Ce code retourne `True` s’il est installé et `False` dans le cas contraire.

```powershell
(Get-ItemProperty "HKLM:SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full").Release -ge 394802
```

### <a name="query-the-registry-using-code"></a>Interroger le registre à l’aide de code

01. Utilisez les <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A?displayProperty=nameWithType> <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A?displayProperty=nameWithType> méthodes et pour accéder à la sous-clé complète du ** \\ \\ programme d’installation de HKEY_LOCAL_MACHINE logiciel Microsoft \\ NET Framework, \\ NDP \\ \\ v4** , dans le Registre Windows.

    > [!IMPORTANT]
    > Si l’application que vous exécutez est 32 bits et s’exécute sous Windows 64 bits, les chemins d’accès au Registre sont différents de ceux indiqués précédemment. Le registre 64 bits est disponible dans la sous-clé **HKEY_LOCAL_MACHINE \\ Software \\ Wow6432Node \\ ** . Par exemple, la sous-clé de Registre pour .NET Framework 4,5 est **HKEY_LOCAL_MACHINE \\ logiciel \\ Wow6432Node \\ Microsoft \\ NET Framework Setup \\ NDP \\ v4 \\ complet**.

01. Vérifiez la valeur REG_DWORD de **version** pour déterminer la version installée. Pour être compatible, recherchez une valeur supérieure ou égale à la valeur listée dans le [tableau des versions du .NET Framework](#version_table).

L’exemple suivant vérifie la valeur de l’entrée de **publication** dans le registre pour rechercher les versions de .NET Framework 4.5-4.8 qui sont installées :

:::code language="csharp" source="snippets/csharp/versions-installed.cs" id="2":::

:::code language="vb" source="snippets/visual-basic/versions-installed.vb" id="2":::

L’exemple affiche une sortie similaire à ce qui suit :

```output
.NET Framework Version: 4.6.1
```

Cet exemple suit la pratique recommandée concernant la vérification de version :

- Il vérifie si la valeur de l’entrée **Release** est *supérieure ou égale à* la valeur des clés de version connues.
- Il effectue sa vérification en partant de la version la plus récente vers la version la plus ancienne.

## <a name="detect-net-framework-10-through-40"></a>Détection des .NET Framework 1,0 à 4,0

Chaque version de .NET Framework de 1,1 à 4,0 est indiquée sous la forme d’une sous-clé dans **HKEY_LOCAL_MACHINE \\ logiciel \\ Microsoft \\ NET Framework Setup \\ NDP**. Le tableau suivant répertorie le chemin d’accès à chaque version de .NET Framework. Pour la plupart des versions, il existe une valeur d' **installation** REG_DWORD de `1` pour indiquer que cette version est installée. Dans ces sous-clés, il y a également une valeur de REG_SZ de **version** qui contient une chaîne de version.

> [!NOTE]
> La sous-clé **d’installation** du .NET Framework dans le chemin d’accès du registre ne commence *pas* par un point.

| Version du Framework  | Sous-clé de Registre | Valeur |
| ------------------ | --------------- | ----- |
| 1.0                | **HKLM \\ Software \\ Microsoft \\ . \\Stratégie NETFramework \\ v 1.0 \\ 3705**     | **Installer** REG_SZ est égal à `1` |
| 1.1                | **HKLM \\ Software \\ Microsoft \\ NET Framework Setup \\ NDP \\ v 1.1.4322**   | **Installer** REG_DWORD est égal à `1` |
| 2.0                | **HKLM \\ Software \\ Microsoft \\ .NET Framework Setup \\ NDP \\ v 2.0.50727**  | **Installer** REG_DWORD est égal à `1` |
| 3.0                | **HKLM \\ Software \\ Microsoft \\ .NET Framework Setup \\ NDP \\ v 3.0 \\ installation** | **InstallSuccess** REG_DWORD est égal à `1` |
| 3,5                | **HKLM \\ Software \\ Microsoft \\ NET Framework Setup \\ NDP \\ v 3.5**        | **Installer** REG_DWORD est égal à `1` |
| Profil client 4,0 | **HKLM \\ Software \\ Microsoft \\ .NET Framework installation de \\ NDP \\ v4 \\ client**  | **Installer** REG_DWORD est égal à `1` |
| Profil complet 4,0   | **HKLM version du \\ \\ \\ programme d’installation de Microsoft NET Framework, \\ NDP \\ v4 \\ complet**    | **Installer** REG_DWORD est égal à `1` |

> [!IMPORTANT]
> Si l’application que vous exécutez est 32 bits et s’exécute sous Windows 64 bits, les chemins d’accès au Registre sont différents de ceux indiqués précédemment. Le registre 64 bits est disponible dans la sous-clé **HKEY_LOCAL_MACHINE \\ Software \\ Wow6432Node \\ ** . Par exemple, la sous-clé de Registre pour .NET Framework 3,5 est **HKEY_LOCAL_MACHINE \\ logiciel \\ Wow6432Node \\ Microsoft \\ NET Framework Setup \\ NDP \\ v 3.5**.

Notez que le chemin d’accès au registre de la sous-clé .NET Framework 1,0 est différent des autres.

### <a name="use-registry-editor-older-framework-versions"></a>Utiliser l’éditeur du Registre (versions antérieures de l’infrastructure)

01. À partir du menu **Démarrer**, choisissez **Exécuter**, entrez *regedit*, puis sélectionnez **OK**.

    Vous devez disposer d’informations d’identification d’administrateur pour exécuter regedit.

01. Ouvrez la sous-clé qui correspond à la version que vous souhaitez vérifier. Utilisez le tableau de la section [détecter les .NET Framework 1,0 à 4,0](#detect-net-framework-10-through-40) .

    L’illustration suivante montre la sous-clé et sa valeur de **version** pour .NET Framework 3,5.

    ![Entrée de Registre pour .NET Framework 3,5.](./media/net-4-and-earlier.png ".NET Framework 3,5 et versions antérieures")

### <a name="query-the-registry-using-code-older-framework-versions"></a>Interroger le registre à l’aide de code (versions antérieures du Framework)

Utilisez la <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> classe pour accéder à la sous-clé ** \\ \\ NDP du \\ programme d’installation \\ de HKEY_LOCAL_MACHINE logiciel Microsoft NET Framework** dans le Registre Windows.

> [!IMPORTANT]
> Si l’application que vous exécutez est 32 bits et s’exécute sous Windows 64 bits, les chemins d’accès au Registre sont différents de ceux indiqués précédemment. Le registre 64 bits est disponible dans la sous-clé **HKEY_LOCAL_MACHINE \\ Software \\ Wow6432Node \\ ** . Par exemple, la sous-clé de Registre pour .NET Framework 3,5 est **HKEY_LOCAL_MACHINE \\ logiciel \\ Wow6432Node \\ Microsoft \\ NET Framework Setup \\ NDP \\ v 3.5**.

L’exemple suivant recherche les versions de .NET Framework 1-4 qui sont installées :

:::code language="csharp" source="snippets/csharp/versions-installed.cs" id="1":::

:::code language="vb" source="snippets/visual-basic/versions-installed.vb" id="1":::

L’exemple affiche une sortie similaire à ce qui suit :

```output
v2.0.50727  2.0.50727.4927  SP2
v3.0  3.0.30729.4926  SP2
v3.5  3.5.30729.4926  SP1
v4.0
  Client  4.0.0.0
```

## <a name="find-clr-versions"></a>Identifier les versions du CLR

La .NET Framework CLR installée avec .NET Framework est gérée séparément. Il existe deux façons de détecter la version du .NET Framework CLR :

- **Outil Clrver.exe**

  Utilisez l' [outil CLR version (Clrver.exe)](../tools/clrver-exe-clr-version-tool.md) pour déterminer quelles versions du CLR sont installées sur un ordinateur. Ouvrez le [invite de commandes développeur pour Visual Studio](../tools/developer-command-prompt-for-vs.md) et entrez `clrver` .

  Exemple de sortie :

  ```console
  Versions installed on the machine:
  v2.0.50727
  v4.0.30319
  ```

- **La `Environment` classe**

  > [!IMPORTANT]
  > Pour .NET Framework 4,5 et versions ultérieures, n’utilisez pas la <xref:System.Environment.Version%2A?displayProperty=nameWithType> propriété pour détecter la version du CLR. Au lieu de cela, interrogez le registre comme décrit dans [détecter les .NET Framework 4,5 et versions ultérieures](#detect-net-framework-45-and-later-versions).

  1. Interrogez la propriété <xref:System.Environment.Version?displayProperty=nameWithType> pour récupérer un objet <xref:System.Version>.

     L’objet `System.Version` retourné identifie la version du runtime qui est en train d’exécuter le code. Il ne retourne pas les versions d’assembly ni d’autres versions du runtime susceptibles d’avoir été installées sur l’ordinateur.

     Pour les versions .NET Framework 4, 4,5, 4.5.1 et 4.5.2, la représentation sous forme de chaîne de l' <xref:System.Version> objet retourné se présente sous la forme 4.0.30319.* xxxxx*, où *xxxxx* est inférieur à 42000. Pour .NET Framework 4,6 et versions ultérieures, il se présente sous la forme 4.0.30319.42000.

  1. Une fois que vous disposez de l’objet de **version** , interrogez-le comme suit :

     - Pour l’identificateur de la version majeure (par exemple, *4* pour la version 4.0), utilisez la propriété <xref:System.Version.Major%2A?displayProperty=nameWithType>.

     - Pour l’identificateur de la version mineure (par exemple, *0* pour la version 4.0), utilisez la propriété <xref:System.Version.Minor%2A?displayProperty=nameWithType>.

     - Pour la chaîne de la version entière (par exemple, *4.0.30319.18010*), utilisez la méthode <xref:System.Version.ToString%2A?displayProperty=nameWithType>. Cette méthode retourne une valeur unique qui reflète la version du runtime qui est en train d’exécuter le code. Elle ne retourne pas les versions d’assembly ni d’autres versions du runtime susceptibles d’être installées sur l’ordinateur.

  L’exemple suivant utilise la propriété <xref:System.Environment.Version%2A?displayProperty=nameWithType> pour récupérer les informations de version du CLR :

  ```csharp
  Console.WriteLine($"Version: {Environment.Version}");
  ```

  ```vb
  Console.WriteLine($"Version: {Environment.Version}")
  ```

  L’exemple affiche une sortie similaire à ce qui suit :

  ```output
  Version: 4.0.30319.18010
  ```

## <a name="see-also"></a>Voir aussi

- [Comment : déterminer les mises à jour de .NET Framework installées](how-to-determine-which-net-framework-updates-are-installed.md)
- [Installer .NET Framework pour les développeurs](../install/guide-for-developers.md)
- [Versions et dépendances de .NET Framework](versions-and-dependencies.md)

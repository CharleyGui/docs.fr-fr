---
title: Élément <loadFromRemoteSources>
ms.date: 05/24/2018
helpviewer_keywords:
- loadFromRemoteSources element
- <loadFromRemoteSources> element
ms.assetid: 006d1280-2ac3-4db6-a984-a3d4e275046a
ms.openlocfilehash: a0dcffe378cdd09de0fbd8f0a6ef0635c033fd9c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154060"
---
# <a name="loadfromremotesources-element"></a>\<chargeDeRemoteSources> élément
Précise si les assemblages chargés de sources éloignées devraient bénéficier d’une pleine confiance dans le cadre .NET 4 et plus tard.
  
> [!NOTE]
> Si vous avez été dirigé vers cet article en raison d’un message d’erreur dans la liste d’erreurs du projet Visual Studio ou d’une erreur de build, voir [Comment : Utilisez une assemblée à partir du Web dans Visual Studio](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ee890038(v=vs.100)).  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<>de temps d’exécution**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<chargeDeRemoteSources>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<loadFromRemoteSources
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`enabled`|Attribut requis.<br /><br /> Précise si un assemblage chargé à partir d’une source éloignée doit bénéficier d’une pleine confiance.|  
  
## <a name="enabled-attribute"></a>attribut activé  
  
|Valeur|Description|  
|-----------|-----------------|  
|`false`|N’accordez pas la pleine confiance aux demandes provenant de sources éloignées. Il s’agit de la valeur par défaut.|  
|`true`|Accorder une confiance totale aux demandes provenant de sources éloignées.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les options d'initialisation du runtime.|  
  
## <a name="remarks"></a>Notes 

Dans le cadre .NET 3.5 et les versions antérieures, si vous chargez un assemblage à partir d’un emplacement éloigné, le code dans l’assemblage fonctionne en fiducie partielle avec un ensemble de subvention qui dépend de la zone à partir de laquelle il est chargé. Par exemple, si vous chargez un assemblage à partir d’un site Web, il est chargé dans la zone Internet et accordé l’ensemble d’autorisation Internet. En d’autres termes, il s’exécute dans un bac à sable Internet.

En commençant par le cadre .NET 4, la politique de sécurité d’accès au code (CAS) est désactivée et les assemblages sont chargés en pleine confiance. Normalement, cela accorderait une pleine confiance aux <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> assemblées chargées de la méthode qui avait déjà été bacée à sable. Pour éviter cela, la possibilité d’exécuter le code dans les assemblages chargés à partir d’une source distante est désactivée par défaut. Par défaut, si vous essayez de <xref:System.IO.FileLoadException> charger un assemblage à distance, un message à l’exception comme ce qui suit est lancé :

```text
System.IO.FileNotFoundException: Could not load file or assembly 'file:assem.dll' or one of its dependencies. Operation is not supported.
(Exception from HRESULT: 0x80131515)
File name: 'file:assem.dll' --->
System.NotSupportedException: An attempt was made to load an assembly from a network location which would have caused the assembly
to be sandboxed in previous versions of the .NET Framework. This release of the .NET Framework does not enable CAS policy by default,
so this load may be dangerous. If this load is not intended to sandbox the assembly, please enable the loadFromRemoteSources switch.
```

Pour charger l’assemblage et exécuter son code, vous devez soit :

- Créez explicitement un bac à sable pour l’assemblage (voir [Comment : Exécuter le code partiellement fiable dans un bac à sable).](../../../misc/how-to-run-partially-trusted-code-in-a-sandbox.md)

- Exécutez le code de l’assemblée en pleine confiance. Vous le faites en `<loadFromRemoteSources>` configurant l’élément. Il vous permet de spécifier que les assemblées qui fonctionnent en partie en fiducie partielle dans les versions antérieures du cadre .NET fonctionnent maintenant en pleine confiance dans le cadre .NET 4 et les versions ultérieures.

> [!IMPORTANT]
> Si l’assemblage ne doit pas fonctionner en pleine confiance, ne définissez pas cet élément de configuration. Au lieu de cela, créer un bac à sable <xref:System.AppDomain> dans lequel charger l’assemblage.

L’attribut `enabled` `<loadFromRemoteSources>` de l’élément n’est efficace que lorsque la sécurité d’accès au code (CAS) est désactivée. Par défaut, la politique de la SAE est désactivée dans le cadre .NET 4 et les versions ultérieures. Si vous `enabled` `true`vous fixez, les assemblages à distance sont accordés pleine confiance.

Si `enabled` elle n’est pas réglée à `true`, a <xref:System.IO.FileLoadException> est jeté sous l’une ou l’autre des conditions suivantes:

- Le comportement de sandboxing du domaine actuel est différent de son comportement dans le cadre .NET 3.5. Cela exige que la politique de la SAE soit désactivée, et que le domaine actuel ne soit pas bac à sable.

- L’assemblage chargé n’est pas de la `MyComputer` zone.

Définir `<loadFromRemoteSources>` l’élément pour `true` empêcher cette exception d’être jeté. Il vous permet de spécifier que vous ne vous fiez pas à l’heure courante pour poncer les assemblages chargés pour la sécurité, et qu’ils peuvent être autorisés à exécuter en pleine confiance.

## <a name="notes"></a>Notes

- Dans le cadre .NET 4.5 et les versions ultérieures, les assemblages sur les actions de réseau local fonctionnent en pleine confiance par défaut; vous n’avez pas `<loadFromRemoteSources>` à activer l’élément.

- Si une application a été copiée sur le Web, elle est signalée par Windows comme étant une application web, même si elle réside sur l’ordinateur local. Vous pouvez modifier cette désignation en modifiant ses `<loadFromRemoteSources>` propriétés de fichiers, ou vous pouvez utiliser l’élément pour accorder à l’assemblée la pleine confiance. Comme alternative, vous pouvez <xref:System.Reflection.Assembly.UnsafeLoadFrom%2A> utiliser la méthode pour charger un assemblage local que le système d’exploitation a signalé comme ayant été chargé à partir du Web.

- Vous pouvez <xref:System.IO.FileLoadException> obtenir une application dans une application qui est en cours d’exécution dans une application Windows Virtual PC. Cela peut se produire lorsque vous essayez de charger un fichier à partir de dossiers liés sur l’ordinateur d’hébergement. Il peut également se produire lorsque vous essayez de charger un fichier à partir d’un dossier lié sur [les services de bureau à distance](/windows/win32/termserv/terminal-services-portal) (Services terminaux). Pour éviter l’exception, définissez `enabled` `true`à .

## <a name="configuration-file"></a>Fichier de configuration

Cet élément est généralement utilisé dans le fichier de configuration d’application, mais peut être utilisé dans d’autres fichiers de configuration en fonction du contexte. Pour plus d’informations, voir l’article [Plus implicite Utilise de la politique casS: loadDeRemoteSources](https://docs.microsoft.com/archive/blogs/shawnfa/more-implicit-uses-of-cas-policy-loadfromremotesources) dans le blog .NET Security.  

## <a name="example"></a> Exemple

L’exemple suivant montre comment accorder une pleine confiance aux assemblées chargées de sources éloignées.

```xml
<configuration>  
   <runtime>  
      <loadFromRemoteSources enabled="true"/>  
   </runtime>  
</configuration>  
```

## <a name="see-also"></a>Voir aussi

- [Utilisations implicites de la politique de la SAE : chargeDeRemoteSources](https://docs.microsoft.com/archive/blogs/shawnfa/more-implicit-uses-of-cas-policy-loadfromremotesources)
- [Guide pratique pour exécuter du code d’un niveau de confiance partiel dans un bac à sable (sandbox)](../../../misc/how-to-run-partially-trusted-code-in-a-sandbox.md)
- [Schéma des paramètres d'exécution](index.md)
- [Configuration Fichier Schema](../index.md)
- <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>

---
title: Élément <useLegacyJit>
ms.date: 04/26/2017
ms.assetid: c2cf97f0-9262-4f1f-a754-5568b51110ad
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3b783a82b1ef964de308532ef544bbfab2397400
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252224"
---
# <a name="uselegacyjit-element"></a>\<useLegacyJit>, élément

Détermine si le common language runtime utilise le compilateur JIT 64 bits hérité pour la compilation juste-à-temps.  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<> d’exécution**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<useLegacyJit>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml
<useLegacyJit enabled=0|1 />
```

Le nom `useLegacyJit` de l’élément respecte la casse.
  
## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
| Attribut | Description                                                                                   |  
| --------- | --------------------------------------------------------------------------------------------- |  
| `enabled` | Attribut requis.<br><br>Spécifie si le runtime utilise le compilateur JIT 64 bits hérité. |  
  
### <a name="enabled-attribute"></a>attribut activé  
  
| `Value` | Description                                                                                                         |  
| ----- | ------------------------------------------------------------------------------------------------------------------- |  
| 0     | Le common language runtime utilise le nouveau compilateur JIT 64 bits inclus dans les .NET Framework 4,6 et versions ultérieures. |  
| 1     | Le common language runtime utilise l’ancien compilateur JIT 64 bits.                                                     |  
  
### <a name="child-elements"></a>Éléments enfants

Aucun
  
### <a name="parent-elements"></a>Éléments parents  
  
| Élément         | Description                                                                                                       |  
| --------------- | ----------------------------------------------------------------------------------------------------------------- |  
| `configuration` | Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework. |  
| `runtime`       | Contient des informations sur les options d'initialisation du runtime.                                                        |  
  
## <a name="remarks"></a>Notes  

À partir de la .NET Framework 4,6, le common language runtime utilise un nouveau compilateur 64 bits pour la compilation juste-à-temps (JIT) par défaut. Dans certains cas, cela peut entraîner une différence de comportement par rapport au code d’application qui a été compilé juste-à-temps par la version précédente du compilateur JIT 64 bits. En affectant `enabled` à `1`l’attribut `<useLegacyJit>` de l’élément la valeur, vous pouvez désactiver le nouveau compilateur JIT 64 bits et compiler à la place votre application à l’aide du compilateur JIT 64 bits hérité.  
  
> [!NOTE]
> L' `<useLegacyJit>` élément affecte uniquement la compilation JIT 64 bits. La compilation avec le compilateur JIT 32 bits n’est pas affectée.  
  
Au lieu d’utiliser un paramètre de fichier de configuration, vous pouvez activer le compilateur JIT 64 bits hérité de deux manières :  
  
- Définition d’une variable d’environnement

  Affectez `COMPLUS_useLegacyJit` `1` à la variable d’environnement (utilisezlenouveaucompilateurJIT64bits)ou(utilisezl’anciencompilateurJIT64bits):`0`
  
  ```  
  COMPLUS_useLegacyJit=0|1  
  ```  
  
  La variable d’environnement a une *portée globale*, ce qui signifie qu’elle affecte toutes les applications exécutées sur l’ordinateur. Si elle est définie, elle peut être remplacée par le paramètre du fichier de configuration de l’application. Le nom de la variable d’environnement n’est pas sensible à la casse.
  
- Ajout d’une clé de Registre

  Vous pouvez activer le compilateur JIT 64 bits hérité en ajoutant une `REG_DWORD` valeur à la `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` clé ou `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` dans le registre. La valeur est nommée `useLegacyJit`. Si la valeur est 0, le nouveau compilateur est utilisé. Si la valeur est 1, le compilateur JIT 64 bits hérité est activé. Le nom de la valeur de registre ne respecte pas la casse.
  
  L’ajout de la valeur `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` à la clé affecte toutes les applications qui s’exécutent sur l’ordinateur. L’ajout de la valeur `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` à la clé affecte toutes les applications exécutées par l’utilisateur actuel. Si un ordinateur est configuré avec plusieurs comptes d’utilisateur, seules les applications exécutées par l’utilisateur actuel sont affectées, sauf si la valeur est également ajoutée aux clés de Registre pour d’autres utilisateurs. L’ajout `<useLegacyJit>` de l’élément à un fichier de configuration remplace les paramètres du Registre, s’ils sont présents.  
  
## <a name="example"></a>Exemple  

Le fichier de configuration suivant désactive la compilation avec le nouveau compilateur JIT 64 bits et utilise à la place le compilateur JIT 64 bits hérité.  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
  <runtime>  
    <useLegacyJit enabled="1" />  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi

- [\<Élément > du Runtime](runtime-element.md)
- [\<configuration>, élément](../configuration-element.md)
- [Atténuation Nouveau compilateur JIT 64 bits](../../../migration-guide/mitigation-new-64-bit-jit-compiler.md)

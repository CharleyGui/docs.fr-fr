---
title: GetCustomUI
ms.date: 03/30/2017
helpviewer_keywords:
- custom error messages [WPF]
ms.assetid: e55180fc-35bb-4f80-a136-772b5eb3e4e5
ms.openlocfilehash: a9c4c9d597f5cc1b172213d49a3dd5b8f1c1f671
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991375"
---
# <a name="getcustomui"></a>GetCustomUI
Appelé par PresentationHost. exe pour recevoir des messages de progression et d’erreur personnalisés de l’hôte, s’il est implémenté.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetCustomUI( [out] BSTR* pwzProgressAssemblyName, [out] BSTR* pwzProgressClassName, [out] BSTR* pwzErrorAssemblyName, [out] BSTR* pwzErrorClassName );  
```  
  
## <a name="parameters"></a>Paramètres  
 `pwzProgressAssemblyName`  
  
 à Pointeur vers l’assembly qui contient l’interface utilisateur de la progression fournie par l’hôte.  
  
 `pwzProgressClassName`  
  
 à Nom de la classe qui est l’interface utilisateur de la progression fournie par l’hôte, [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] de préférence <xref:System.Windows.Controls.Page> un fichier avec est son élément de niveau supérieur. Cette classe réside dans l’assembly spécifié par `pwzProgressAssemblyName`.  
  
 `pwzErrorAssemblyName`  
  
 à Pointeur vers l’assembly qui contient l’interface utilisateur d’erreur fournie par l’hôte.  
  
 `pwzErrorClassName`  
  
 à Nom de la classe qui est l’interface utilisateur d’erreur fournie par l’hôte, de préférence un fichier <xref:System.Windows.Controls.Page> XAML avec est son élément de niveau supérieur. Cette classe réside dans l’assembly spécifié par `pwzErrorAssemblyName`.  
  
## <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour  
 HRESULT : Ignoré.  
  
## <a name="remarks"></a>Notes  
 Une application hôte peut avoir un thème spécifique auquel les interfaces utilisateur par défaut de PresentationHost. exe peuvent ne pas se conformer. Si c’est le cas, l’application hôte peut implémenter [GetCustomUI](getcustomui.md) pour retourner les interfaces utilisateur de progression et d’erreur à PresentationHost. exe. PresentationHost. exe appellera toujours [GetCustomUI](getcustomui.md) avant d’utiliser ses interfaces utilisateur par défaut.  
  
 Cette fonction est appelée une fois pendant l’initialisation de PresentationHost.  
  
## <a name="see-also"></a>Voir aussi

- [IWpfHostSupport](iwpfhostsupport.md)

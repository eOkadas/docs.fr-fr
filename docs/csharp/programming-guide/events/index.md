---
title: Événements - Guide de programmation C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- classes [C#], events
- C# language, events
- events [C#]
ms.assetid: a8e51b22-d294-44fb-9539-0072f06c4cb3
ms.openlocfilehash: 7a8a8e6b6a393f151d69d1879f475e04f44df5fa
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69590382"
---
# <a name="events-c-programming-guide"></a>Événements (Guide de programmation C#)
Les événements permettent à une [classe](../../language-reference/keywords/class.md) ou à un objet de notifier d’autres classes ou objets quand quelque chose de significatif se produit. La classe qui envoie (ou *déclenche*) l’événement est appelée *publieur* et les classes qui reçoivent (ou *gèrent*) l’événement sont appelées *abonnés*.  
  
 Dans une application C# Windows Forms ou web classique, vous vous abonnez à des événements déclenchés par des contrôles, comme des boutons et des zones de liste. Vous pouvez utiliser l’IDE Visual C# pour parcourir les événements publiés par un contrôle et sélectionner ceux que vous voulez gérer. L’IDE permet d’ajouter automatiquement une méthode de gestionnaire d’événements vide et le code pour vous abonner à l’événement. Pour plus d'informations, voir [Procédure : s’abonner et se désabonner d’événements](./how-to-subscribe-to-and-unsubscribe-from-events.md).  
  
## <a name="events-overview"></a>Vue d'ensemble des événements  
 Les événements ont les propriétés suivantes :  
  
- Le publieur détermine quand un événement est déclenché ; les abonnés déterminent l’action entreprise en réponse à l’événement.  
  
- Un événement peut avoir plusieurs abonnés. Un abonné peut gérer plusieurs événements provenant de plusieurs publieurs.  
  
- Les événements qui n’ont aucun abonné ne sont jamais déclenchés.  
  
- Les événements sont généralement utilisés pour signaler des actions de l’utilisateur, comme les clics de bouton ou les sélections de menu dans les interfaces utilisateur graphiques.  
  
- Quand un événement a plusieurs abonnés, les gestionnaires d’événements sont appelées de façon synchrone quand un événement est déclenché. Pour appeler des événements de façon asynchrone, consultez [Calling Synchronous Methods Asynchronously](../../../standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md).  
  
- Dans la bibliothèque de classes .NET Framework, les événements sont basés sur le délégué <xref:System.EventHandler> et la classe de base <xref:System.EventArgs>.  
  
## <a name="related-sections"></a>Rubriques connexes  
 Pour plus d'informations, voir :  
  
- [Guide pratique pour s’abonner et se désabonner d’événements](./how-to-subscribe-to-and-unsubscribe-from-events.md)  
  
- [Guide pratique pour publier des événements conformes aux indications du .NET Framework](./how-to-publish-events-that-conform-to-net-framework-guidelines.md)  
  
- [Guide pratique pour déclencher les événements de la classe de base dans les classes dérivées](./how-to-raise-base-class-events-in-derived-classes.md)  
  
- [Guide pratique pour  implémenter des événements d’interface](./how-to-implement-interface-events.md)  
  
- [Guide pratique pour implémenter des accesseurs d’événement personnalisés](./how-to-implement-custom-event-accessors.md)  
  
## <a name="c-language-specification"></a>Spécification du langage C#  

Pour plus d’informations, consultez [Événements](~/_csharplang/spec/classes.md#events) dans la [Spécification du langage C#](../../language-reference/language-specification/index.md). La spécification du langage est la source de référence pour la syntaxe C# et son utilisation.
  
## <a name="featured-book-chapters"></a>Chapitres proposés  
 [Delegates, Events, and Lambda Expressions](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) (Délégués, événements et expressions lambda) dans [C# 3.0 Cookbook, Third Edition: More than 250 solutions for C# 3.0 programmers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)  
  
 [Delegates and Events](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652490%28v=orm.10%29) dans [Learning C# 3.0: Master the fundamentals of C# 3.0](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652493%28v=orm.10%29)  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.EventHandler>
- [Guide de programmation C#](../index.md)
- [Délégués](../delegates/index.md)
- [Création de gestionnaires d’événements dans les Windows Forms](../../../framework/winforms/creating-event-handlers-in-windows-forms.md)

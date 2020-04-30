---
description: Vous pouvez configurer des boutons qui appellent les méthodes TVSDK pour suspendre et lire le média.
seo-description: Vous pouvez configurer des boutons qui appellent les méthodes TVSDK pour suspendre et lire le média.
seo-title: Mise en oeuvre d’un bouton Lecture/Pause
title: Mise en oeuvre d’un bouton Lecture/Pause
uuid: eccdce4b-0114-4389-b5ee-74fe62d38ed8
translation-type: tm+mt
source-git-commit: ''

---


# Mise en oeuvre d’un bouton Lecture/Pause{#implement-a-play-pause-button}

Vous pouvez configurer des boutons qui appellent les méthodes TVSDK pour suspendre et lire le média.

Utilisez l’exemple de code suivant pour mettre en oeuvre un bouton de lecture ou de pause :

<!--<a id="example_BC2632D673FE451190A30A23145090D0"></a>-->

```
_playPauseButton =  
[[UIButton alloc] initWithFrame:CGRectMake(BUTTON_POS_X, BUTTON_POS_Y, BUTTON_SIZE_W, BUTTON_SIZE_H)]; 
[_playPauseButton setImage:[UIImage imageNamed:@"play.png"] forState:UIControlStateNormal];  
[_playPauseButton setImage:[UIImage imageNamed:@"pause.png"] forState:UIControlStateSelected]; 
[_playPauseButton addTarget:self action:@selector(playTouch:) forControlEvents:UIControlEventTouchUpInside]; 
[self addSubview:_playPauseButton]; 
 
... 
 
- (void)playTouch:(id)sender { 
    if (self.player.status == PTMediaPlayerStatusPlaying) { 
        _playPauseButton.selected = YES;  
        [self.player pause]; 
    } 
    else { 
        _playPauseButton.selected = NO; [self.player play]; 
    } 
} 
```


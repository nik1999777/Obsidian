![[Untitled 27.png|Untitled 27.png]]

Мы можем использовать **inline стили** в **React**. То есть назначать **стили** непосредственно в верстке. Но это не очень хорошая практика.

**Стили** лучше назначать через **классы**.

```JavaScript
<span className="list-group-item-label" 
    onClick={onToggleProp} 
    data-toggle="rise"
    style={{fontSize: '40px', color: 'red', transition: 'all', WebkitTransition: 'all', msTransition: 'all'}}>{name}</span>
```
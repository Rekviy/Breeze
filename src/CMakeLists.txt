# application

set(GAME_SOURCE src/Breeze.cpp
src/gameLayer.cpp
src/ui/gameUI.cpp
src/cameraWrapper.cpp
src/ui/button.cpp
src/ui/themeManager.cpp
src/ui/interactElement.cpp
src/ui/counter.cpp
src/ui/objectPool.cpp
src/ui/grid.cpp
src/ui/maskLayer.cpp
src/ui/ship.cpp
src/gridManager.cpp
src/gameStateMachine.cpp
)
set(GAME_HEADER 
src/gameLayer.h
src/ui/gameUI.h
src/cameraWrapper.h
src/ui/button.h
src/ui/themeManager.h
src/ui/interactElement.h
src/ui/counter.h
src/ui/objectPool.h
#src/ui/IObjectPool.h
src/ui/grid.h
src/ui/maskLayer.h
src/ui/ship.h
src/gridManager.h
src/stateMachine.h
src/gameStateMachine.h
)
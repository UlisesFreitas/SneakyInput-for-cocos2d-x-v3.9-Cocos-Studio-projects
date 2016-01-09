# SneakyInput-for-cocos2d-x-v3.9-Cocos-Studio-projects

SneakyJoystick
==============

SneakyJoystick is a library that provides a 'joystick-like' features to a layer in Cocos2d-x. The library support:

- Joystick Thumb
- Joystick D-Pad
- Regular Buttons
- Holdable Buttons
- Toggleable Buttons

The project was originally created CJ Hanson (https://github.com/cjhanson). This is a port for Cocos2d-x version 2.2.1 and 3.0rc0, and now 3.9 cocos studio projects

How to Use the Library
======================

The best way to use the library is to create a JoystickLayer, and then add that layer to your Game Scene.

This is an example on how to create a Joystick Thumb


How to implement on my game:

In case the HelloWorld i.e

On HelloWorld.h

Add 
remember to put #before include clause
- #include "SneakyButton.h"
- #include "SneakyButtonSkinnedBase.h"
- #include "SneakyJoystickSkinnedBase.h"

Below
public:
    
    SneakyJoystick *leftJoystick;
    SneakyButton *jumpBtn;

HelloWorld.cpp
Add

Rect joystickBaseDimensions;
    joystickBaseDimensions = Rect(0, 0, 160.0f, 160.0f);
    
    Point joystickBasePosition;
    joystickBasePosition = Vec2(visibleSize.width * 0.2f, visibleSize.height*0.2f);
    
    SneakyJoystickSkinnedBase *joystickBase = new SneakyJoystickSkinnedBase();
    joystickBase->init();
    joystickBase->setPosition(joystickBasePosition);
    joystickBase->setBackgroundSprite(Sprite::create("res/joystick-back.png"));
    joystickBase->setThumbSprite(Sprite::create("res/stick.png"));
    
    SneakyJoystick *aJoystick = new SneakyJoystick();
    aJoystick->initWithRect(joystickBaseDimensions);
    
    aJoystick->autorelease();
    joystickBase->setJoystick(aJoystick);
    joystickBase->setPosition(joystickBasePosition);
    
    leftJoystick = joystickBase->getJoystick();
    leftJoystick->retain();
    this->addChild(joystickBase);
    
    And for button
    
    Rect jumpButtonDimensions = Rect(0, 0, 64.0f, 64.0f);
    Point jumpButtonPosition;
    jumpButtonPosition = Vec2(visibleSize.width * 0.9f, visibleSize.height * 0.2f);
    
    SneakyButtonSkinnedBase *jumpButtonBase = new SneakyButtonSkinnedBase();
    jumpButtonBase->init();
    jumpButtonBase->setPosition(jumpButtonPosition);
    
    jumpButtonBase->setDefaultSprite(Sprite::create("res/btn-attack.png"));
    jumpButtonBase->setActivatedSprite(Sprite::create("res/btn-attack-pressed.png"));
    jumpButtonBase->setDisabledSprite(Sprite::create("res/btn-attack-pressed.png"));
    jumpButtonBase->setPressSprite(Sprite::create("res/btn-attack-pressed.png"));
    
    SneakyButton *ajumpButton = new SneakyButton();
    ajumpButton->initWithRect(jumpButtonDimensions);
    ajumpButton->autorelease();
    
    jumpButtonBase->setButton(ajumpButton);
    jumpButtonBase->setPosition(jumpButtonPosition);
    
    jumpBtn = jumpButtonBase->getSbutton();
    jumpBtn->retain();
    this->addChild(jumpButtonBase);
    

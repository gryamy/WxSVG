# WxSVG for AndroidStudio
如何在AndroidStudio上部署WxSVG？

一、在主subproject的build.gradle中添加

    buildscript {
        repositories {
            maven {
                url uri('https://raw.githubusercontent.com/gryamy/WxSVG/master/maven/')
            }
        }
        dependencies {
            classpath 'com.tencent.mm:WxSVGPlugin:0.5'
        }
    }
    repositories {
        maven {
            url uri('https://raw.githubusercontent.com/gryamy/WxSVG/master/maven/')
        }
    }
    dependencies {
        compile 'com.tencent.mm:WxSVGLibrary:0.5'
    }

    apply plugin: 'com.tencent.mm.WxSVG'

二、在自定义的Application.onCreate()中调用

    SVGResourceLoader.load(this);

如此即可使用WxSVG

工具支持WxSVGCode和WxSVGLibrary两个不同的SVG支持方式

只需在build.gradle添加如下代码，然后进行编译即可切换不同的支持方式

    WxSVG {
        open false   		// If false, you'll render .svg in runtime with libwechatsvg.so. Default is true
    }

此外还支持的一些属性

    WxSVG {
        open false   		// If false, you'll render .svg in runtime with libwechatsvg.so
        verbose false		// 是否开启verbose日志
        clean()				// 是否clean生成代码的目录
        ...
    }

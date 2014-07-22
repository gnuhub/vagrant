why
==========
```
* 开发环境复杂，需要一个开发环境搭建工具
* 可以跨平台分发
* 以vagrant源码为范例深入学习vagrant用法，提高开发效率
* 以vagrant作为kiwi开发的原型系统
* 以vagrant源码深入学习ruby
* 以vagrant源码深入学习virtualbox用法
```


# Vagrant
```
n. 流浪者,漂泊者
```
* Website: [http://www.vagrantup.com](http://www.vagrantup.com) 官方网站
* Source: [https://github.com/mitchellh/vagrant](https://github.com/mitchellh/vagrant) 源码
* IRC: `#vagrant` on Freenode IRC聊天频道
* Mailing list: [Google Groups](http://groups.google.com/group/vagrant-up) 邮件列表

Vagrant is a tool for building and distributing development environments.
```
Vagrant是一个构建和分发开发环境的工具
```
Development environments managed by Vagrant can run on local virtualized
platforms such as VirtualBox or VMware, in the cloud via AWS or OpenStack,
or in containers such as with Docker or raw LXC.
```
由Vagrant管理的开发环境可以运行在本地的虚拟化平台，比如VirtualBox VMvare
也可以运行在AWS openstack云平台
也可以运行在docker或者纯LXC等容器中
```

Vagrant provides the framework and configuration format to create and
manage complete portable development environments. These development
environments can live on your computer or in the cloud, and are portable
between Windows, Mac OS X, and Linux.
```
Vagrant 提供了创建 管理完整的可移植的开发环境的框架和配置格式
这些开发环境可以运行在你的电脑或云中，而且可以在windows Mac OS X以及linux之间移植
```

## Quick Start
```
快速入门
```

For the quick-start, we'll bring up a development machine on
[VirtualBox](http://www.virtualbox.org) because it is free and works
on all major platforms. 
```
为了快速入门，我们将在virtualbox上启动一个开发机因为virtualbox是免费的并且可以运行在各种平台
```
Vagrant can, however, work with almost any system such as OpenStack, VMware, Docker, etc.
```
vagrant 还可以跟其他系统openstack vmvare docker协作
```

First, make sure your development machine has
[VirtualBox](http://www.virtualbox.org)
installed. After this,
[download and install the appropriate Vagrant package for your OS](http://www.vagrantup.com/downloads).
```
首要，要确保你的机器安装了virtualbox,然后下载你的系统需要的vagrant安装包
```
To build your first virtual environment:
```
构建你的第一个虚拟开发环境，执行以下命令
```
```
vagrant init hashicorp/precise32
vagrant up
```

Note: The above `vagrant up` command will also trigger Vagrant to download the
`precise32` box via the specified URL. 
```
注：上面的vagrant up命令也将触发vagrant通过网络下载precise32的box
```

Vagrant only does this if it detects that the box doesn't already exist on your system.
```
vagrant仅在你指定的box不存在时才去下载
```

## Getting Started Guide
```
入门指南
```

To learn how to build a fully functional development environment, follow the
[getting started guide](http://docs.vagrantup.com/v2/getting-started/index.html).
```
学习如何构建一个完整的复杂开发环境，请学习文档 入门指南
```
## Installing the Gem from Git
```
从git源码安装gem
```

If you want the bleeding edge version of Vagrant, we try to keep master pretty stable
and you're welcome to give it a shot. 
```
如果你想安装最新的vagrant,我们已经尽量保持主干分支稳定，你可以尝试一下
```

The following is an example showing how to do this:
```
执行下面的命令可以从源码安装
```

    rake install

Ruby 2.0 is needed.
```
Ruby 2.0已经安装
```

## Contributing to Vagrant
```
向vagrant提交代码
```

### Dependencies and Unit Tests
```
依赖和单元测试
```

To hack on vagrant, you'll need [bundler](http://github.com/carlhuda/bundler) which can
be installed with a simple `gem install bundler`. 
```
为了可以修改vagrant,你需要bundler，你可以通过 gem install bundler 安装
```
Afterwards, do the following:
```
然后执行以下命令
```

    bundle install
    rake

This will run the unit test suite, which should come back all green! Then you're good to go!
```
这将运行单元测试套件，应该是卢瑟全部通过，这样你可以继续
```

If you want to run Vagrant without having to install the gem, you may use `bundle exec`,
like so:
```
如果你不想安装vagrant gem想运行，你可以使用 bundle exec
```

    bundle exec vagrant help

**NOTE:** By default running Vagrant in via `bundle` will disable plugins.
```
注 使用bundle运行vagrant将禁用插件
```
This is necessary because Vagrant creates its own private Bundler context
(it does not respect your Gemfile), because it uses Bundler to manage plugin
dependencies.
```
这是必要的因为bundler将创建一个bundler上下文，它不检查你的Gemfile,因为它用bundler管理插件的依赖
```

### Acceptance Tests
```
认可的测试
```

Vagrant also comes with an acceptance test suite that does black-box
tests of various Vagrant components. Note that these tests are **extremely
slow** because actual VMs are spun up and down. The full test suite can
take hours. Instead, try to run focused component tests.

To run the acceptance test suite, first copy `vagrant-spec.config.example.rb`
to `vagrant-spec.config.rb` and modify it to valid values. The places you
should fill in are clearly marked.

Next, see the components that can be tested:

```
$ rake acceptance:components
cli
provider/virtualbox/basic
...
```

Then, run one of those components:

```
$ rake acceptance:run COMPONENTS="cli"
...
```

---
layout: post
title: "Rails 3 generators in gem"
date: 2013-08-11 18:02
comments: true
tags: [code, rubyOnRails, gems]
categories: Rails

keywords: "rails 3, rails generators, gem , github, rails generators gem"
description: "Rails 3 generators in gem"
 
---
---

<!--more-->
### This is the folders structure in a gem.

{% highlight shell %}
lib
  - generators
    - gemname
      install_generator.rb
      - templates
        (template files)
        
{% endhighlight %}

### Install Generator

{% highlight ruby %}

require 'rails/generators'

module ModuleName
  module Generators
    class InstallGenerator < Rails::Generators::NamedBase
      include Rails::Generators::Migration
      
      source_root File.expand_path("../templates", __FILE__)
      
      generators...
      
      def self.next_migration_number(path)
          @migration_number = current_migration_number(path) + 1
          ActiveRecord::Migration.next_migration_number(@migration_number)
      end
  
    end
   
  end
end

{% endhighlight %}


### Generators
{% highlight ruby %}
def generators
           
    generate("controller" , "nameOfController")
    
    copy_file "fileWantYouCopy.rb"   , "app/models/destiniAndNameToCopiedFile.rb"
    
    migration_template("modelOfMigrate.rb"  , "db/migrate/modelOfMigrateDestini.rb")
end
{% endhighlight %}

### Migration template

You need add this include to use migration_template
{% highlight ruby %}
include Rails::Generators::Migration
{% endhighlight %}

You need to implement next_migration_number
{% highlight ruby %}
def self.next_migration_number(path)
      @migration_number = current_migration_number(path) + 1
      ActiveRecord::Migration.next_migration_number(@migration_number)
end
{% endhighlight %}
---
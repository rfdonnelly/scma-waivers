# frozen_string_literal: true

require "bundler/gem_tasks"
require "minitest/test_task"

Minitest::TestTask.create

require "standard/rake"

task default: %i[test standard]

task "smartwaivers.yml" do
  sh "smartwaiver2yaml >smartwaivers.yml"
end

file "waivers.yml" => "smartwaivers.yml" do
  sh "minifyaml <smartwaivers.yml >waivers.yml"
end

file "waivers.csv" => "waivers.yml" do
  sh "yaml2csv <waivers.yml >waivers.csv"
end

file "waivers.pdf" => "waivers.yml" do
  sh "yaml2pdf <waivers.yml >waivers.pdf"
end

task "upload" => %w[waivers.csv waivers.pdf] do
  sh "waivers2scma"
end

task "update-waivers" => "upload"

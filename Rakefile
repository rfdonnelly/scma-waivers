# frozen_string_literal: true

require "bundler/gem_tasks"
require "minitest/test_task"

Minitest::TestTask.create

require "standard/rake"

task default: %i[test standard]

multitask "smartwaivers_raw.yml" do
  sh "smartwaiver2yaml >smartwaivers_raw.yml"
end

multitask "paperwaivers.yml" do
  sh "gsheets2yaml >paperwaivers.yml"
end

file "smartwaivers.yml" => "smartwaivers_raw.yml" do
  sh "minifyaml <smartwaivers_raw.yml >smartwaivers.yml"
end

file "waivers.yml" => ["paperwaivers.yml", "smartwaivers.yml"] do
  sh "mergewaivers paperwaivers.yml smartwaivers.yml >waivers.yml"
end

multitask "gsheets" => "waivers.yml" do
  sh "yaml2gsheets <waivers.yml"
end

file "waivers.csv" => "waivers.yml" do
  sh "yaml2csv <waivers.yml >waivers.csv"
end

file "waivers.pdf" => "waivers.yml" do
  sh "yaml2pdf <waivers.yml >waivers.pdf"
end

multitask "upload" => %w[waivers.csv waivers.pdf] do
  sh "waivers2scma"
end

multitask "update-waivers" => "upload"

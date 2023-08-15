cmake_minimum_required(VERSION 3.16)
project(ChangelogFragmentsCreator VERSION 1.2)

install(FILES ../changelog-creator DESTINATION bin)

# General
set(CPACK_RESOURCE_FILE_LICENSE "${CMAKE_CURRENT_SOURCE_DIR}/../LICENSE")
set(CPACK_RESOURCE_FILE_README "${CMAKE_CURRENT_SOURCE_DIR}/../README.md")
set(CPACK_DEBIAN_PACKAGE_MAINTAINER "Florian Paul Azim <gyptazy> Hoberg <gyptazy@gyptazy.ch>")
set(CPACK_PACKAGE_CONTACT "Florian Paul Azim Hoberg <gyptazy@gyptazy.ch)")
set(CPACK_PACKAGE_VENDOR "gyptazy")

# RPM packaging
set(CPACK_PACKAGE_VERSION ${CMAKE_PROJECT_VERSION})
set(CPACK_GENERATOR "RPM")
set(CPACK_RPM_PACKAGE_ARCHITECTURE "noarch")
set(CPACK_PACKAGE_NAME "changelog-fragments-creator")
set(CPACK_RPM_PACKAGE_SUMMARY "changelog-creater - A tool to create a complete changelog by changelog fragments.")
set(CPACK_RPM_PACKAGE_DESCRIPTION "changelog-creater - A tool to create a complete changelog by changelog fragments.")
set(CPACK_RPM_CHANGELOG_FILE "${CMAKE_CURRENT_SOURCE_DIR}/rpm_changelog.txt")
set(CPACK_PACKAGE_RELEASE 1)
set(CPACK_RPM_PACKAGE_LICENSE "GPL 3.0")
set(CPACK_RPM_PACKAGE_REQUIRES "python >= 3.2.0, python3-pyyaml")

# DEB packaging
set(CPACK_DEBIAN_FILE_NAME DEB-DEFAULT)
set(CPACK_DEBIAN_PACKAGE_ARCHITECTURE "noarch")
set(CPACK_DEBIAN_PACKAGE_SUMMARY "changelog-creater - A tool to create a complete changelog by changelog fragments.")
set(CPACK_DEBIAN_PACKAGE_DESCRIPTION "changelog-creater - A tool to create a complete changelog by changelog fragments.")
set(CPACK_DEBIAN_PACKAGE_CONTROL_EXTRA "${CMAKE_CURRENT_SOURCE_DIR}/deb_changelog.txt")
set(CPACK_DEBIAN_PACKAGE_REQUIRES "python3-yaml")
set(CPACK_DEBIAN_PACKAGE_LICENSE "GPL 3.0")


# FreeBSD packaging
set(CPACK_FREEBSD_PACKAGE_ARCHITECTURE "noarch")
set(CPACK_FREEBSD_PACKAGE_SUMMARY "changelog-creater - A tool to create a complete changelog by changelog fragments.")
set(CPACK_FREEBSD_PACKAGE_DESCRIPTION "changelog-creater - A tool to create a complete changelog by changelog fragments.")
set(CPACK_FREEBSD_PACKAGE_CONTROL_EXTRA "${CMAKE_CURRENT_SOURCE_DIR}/fbsd_changelog.txt")
set(CPACK_FREEBSD_PACKAGE_REQUIRES "python3-yaml")
set(CPACK_FREEBSD_PACKAGE_LICENSE "GPL 3.0")


# Install
set(CPACK_PACKAGING_INSTALL_PREFIX ${CMAKE_INSTALL_PREFIX})
include(CPack)

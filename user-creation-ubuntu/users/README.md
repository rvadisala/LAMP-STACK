Notes:

Alternatives for sudoers:
    - name: Add user to sudoers
      copy:
        dest: "/etc/sudoers.d/{{ item.name }}"
        content: "{{ item.name }} ALL=(ALL) NOPASSWD: ALL"
      with_items: "{{ users }}"
      when: item.sudo == true

    - name: Remove user from sudoers
      file:
        path: "/etc/sudoers.d/{{ item.name }}"
        state: absent
      with_items: "{{ users }}"
      when: item.sudo == false


user deletion:
  users_absent: [] -- When no users to delete

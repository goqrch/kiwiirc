<template>
    <li
        :class="[
            nicklist.userMode(user) ? 'kiwi-nicklist-user--mode-' + nicklist.userMode(user) : '',
            user.away ? 'kiwi-nicklist-user--away' : ''
        ]"
        class="kiwi-nicklist-user"
        @click="nicklist.openUserbox(user)"
    >
        <span class="kiwi-nicklist-user-prefix">{{ nicklist.userModePrefix(user) }}</span>
        <span :style="nicklist.nickStyle(user.nick)"
              class="kiwi-nicklist-user-nick"
        >{{ user.nick }}
        </span>
        <span class="kiwi-nicklist-messageuser" @click.stop="nicklist.openQuery(user)">
            <i class="fa fa-comment" aria-hidden="true"/>
        </span>
    </li>
</template>

<script>

'kiwi public';

export default {
    props: ['user', 'nicklist'],
};
</script>

<style>

.kiwi-nicklist-user {
    line-height: 40px;
    padding: 0 1em;
    margin: 0;
    position: relative;
    box-sizing: border-box;
}

.kiwi-nicklist-user-nick {
    font-weight: bold;
    cursor: pointer;
}

.kiwi-nicklist-messageuser {
    position: absolute;
    content: '\f075';
    right: 1em;
    font-family: fontAwesome, sans-serif;
    top: 50%;
    margin-top: -1.5em;
    opacity: 0;
}

.kiwi-nicklist-messageuser:hover {
    cursor: pointer;
}

.kiwi-nicklist-user:hover .kiwi-nicklist-messageuser {
    opacity: 1;
}

</style>

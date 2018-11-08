# upgrade-to-20-notice

<table>
  <thead>
    <tr>
      <th style="text-align:left">
        <img src="../../.gitbook/assets/info-sign.svg" alt/>
      </th>
      <th style="text-align:left">
        <p><b>Important note</b>
          <br />
        </p>
        <p>Please note that during upgrade procedure <b>old rules and plugins</b> will
          be <b>completely removed</b> from your ThingsBoard instance.</p>
        <p>Old rules and plugins functionality is replaced by <b>new rule engine components</b> (rule
          chains and rule nodes).</p>
        <p>If you have configured rules or plugins you need to backup them using
          export function before performing upgrade. After upgrade you will need
          to configure new rule chains in order to restore your application logic
          performed by old rules/plugins.</p>
        <p>Please refer to <a href="https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/user-guide/rule-engine-2-0/re-getting-started/README.md">new rule engine</a> documentation
          for details.</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>